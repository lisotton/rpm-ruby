rpm-ruby
========

An RPM spec file to build and install Ruby 2.0 on RHEL.

To build:

```
sudo yum -y install rpmdevtools && rpmdev-setuptree

sudo yum -y install readline libyaml libyaml-devel readline-devel ncurses ncurses-devel gdbm gdbm-devel glibc-devel tcl-devel gcc unzip openssl-devel db4-devel byacc make libffi-devel

wget https://raw.github.com/nmilford/rpm-ruby/master/ruby.spec -O ~/rpmbuild/SPECS/ruby.spec

wget http://cache.ruby-lang.org/pub/ruby/ruby-%{_rubyver}-%{_rubyminorver}.tar.gz -O ~/rpmbuild/SOURCES/ruby-%{_rubyver}-%{_rubyminorver}.tar.gz

QA_RPATHS=$[ 0x0001|0x0010 ] rpmbuild -bb ~/rpmbuild/SPECS/ruby.spec --define '_rubyver 2.0.0' --define '_rubyminorver p598'
```