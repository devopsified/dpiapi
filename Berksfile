source "https://supermarket.chef.io"

cookbook 'ohai', '~> 2.0.1'
cookbook 'curl', '~> 2.0.1'

#cookbook 'build-essential'
#cookbook 'influxdb', git: 'https://github.com/SimpleFinance/chef-influxdb.git'
#cookbook 'statsd', git: 'https://github.com/librato/statsd-cookbook.git'
#cookbook 'htpasswd', git: 'https://github.com/Youscribe/htpasswd-cookbook.git'
#cookbook 'chef_profiler', git: 'https://github.com/pythian/chef_profiler.git'
#cookbook 'java', '1.29.0'
#cookbook 'mysql', :git => 'git://github.com/opscode-cookbooks/mysql.git'
#cookbook 'nginx', :git => 'git://github.com/opscode-cookbooks/nginx.git'
#cookbook 'memcached', '~> 1.7.2'


Dir.glob(File.join(File.dirname(__FILE__), 'site-cookbooks/*')).each do |cb|
    if ::File.directory?(cb)
        cookbook File.basename(cb), path: cb
    end
end
