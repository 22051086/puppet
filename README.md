# puppet


class apache { 
package  {'httpd':
ensure => installed,
}

file{'/etc/httpd/conf/httpd.conf':
source => 'puppet:///modules/apache/httpd.conf', 
require => Package['httpd'],
}

service { httpd: 
ensure =>running, 
enable => true,
require => File['/etc/httpd/conf/httpd.conf'],
}
