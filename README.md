# Mediawiki module for Puppet

## Description

This module deploys and manages multiple mediawiki instances using a single mediawiki installation. This module has been designed and tested for CentOS 6, Red Hat Enterprise Linux 6, Debian Squeeze, Debian Wheezy, and Ubuntu Precise.

## Usage

First, install the mediawiki package which will be used by all wiki instances:

    class { 'mediawiki':
      admin_email      => 'admin@puppetlabs.com',
      db_root_password => 'really_really_long_password',
      max_memory       => '1024'
    }
    
Next, create an individual wiki instance:

    mediawiki::instance { 'my_wiki1':
      db_password => 'super_long_password',
      db_name     => 'wiki1',
      db_user     => 'wiki1_user'
      port        => '80',
      status      => 'present'
    }

Using this module, one can create multiple independent wiki instances. To create another wiki instance, add the following puppet code:

    mediawiki::instance { 'my_wiki2':
      db_password => 'another_super_long_password',
      db_name     => 'another_wiki',
      db_user     => 'another_wiki_user'
      port        => '80',
      status      => 'present'
    }

## Reference

This module is based on puppet-mediawiki by carlasouza available at
https://github.com/carlasouza/puppet-mediawiki. Others who contributed to this
module include James Turnbull and Zach Leslie.
