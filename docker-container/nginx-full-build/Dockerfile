FROM ubuntu:xenial
MAINTAINER kizkoh

RUN apt-get -yq update && \
    apt-get -yq install software-properties-common build-essential libpcre3-dev libssl-dev git curl ruby2.3 wget bison

# Download nginx source
RUN cd /usr/local/src && \
    curl -L http://nginx.org/download/nginx-1.11.5.tar.gz -O && \
    tar xvf nginx-1.11.5.tar.gz

RUN cd /usr/local/src/nginx-1.11.5 && \
    ./configure --prefix=/usr/local \
                --with-http_v2_module \
		--with-cc-opt='-g -O2' \
		--with-ld-opt='-Wl,-z,relro -Wl,-z,now' \
		--prefix=/usr/share/nginx \
		--conf-path=/etc/nginx/nginx.conf \
		--http-log-path=/var/log/nginx/access.log \
		--error-log-path=/var/log/nginx/error.log \
		--lock-path=/var/lock/nginx.lock \
		--pid-path=/run/nginx.pid \
		--modules-path=/usr/lib/nginx/modules \
		--http-client-body-temp-path=/var/lib/nginx/body \
		--http-fastcgi-temp-path=/var/lib/nginx/fastcgi \
		--http-proxy-temp-path=/var/lib/nginx/proxy \
		--http-scgi-temp-path=/var/lib/nginx/scgi \
		--http-uwsgi-temp-path=/var/lib/nginx/uwsgi \
		--with-debug \
		--with-pcre-jit \
		--with-ipv6 \
		--with-http_ssl_module \
		--with-http_stub_status_module \
		--with-http_realip_module \
		--with-http_auth_request_module \
		--with-http_v2_module \
		--with-http_dav_module \
		--with-http_slice_module \
		--with-threads \
		--with-http_addition_module
		--with-http_geoip_module=dynamic
		--with-http_gunzip_module
		--with-http_gzip_static_module
		--with-http_image_filter_module=dynamic
		--with-http_sub_module
		--with-http_xslt_module=dynamic
		--with-stream=dynamic
		--with-stream_ssl_module
		--with-mail=dynamic
--with-mail_ssl_module
--add-dynamic-module=/build/nginx-7jgWGO/nginx-1.10.1/debian/modules/nginx-auth-pam
--add-module=/build/nginx-7jgWGO/nginx-1.10.1/debian/modules/nginx-dav-ext-module
--add-dynamic-module=/build/nginx-7jgWGO/nginx-1.10.1/debian/modules/nginx-echo
--add-dynamic-module=/build/nginx-7jgWGO/nginx-1.10.1/debian/modules/nginx-upstream-fair
--add-dynamic-module=/build/nginx-7jgWGO/nginx-1.10.1/debian/modules/ngx_http_substitutions_filter_module


&& \
#     make && \
#     make install
    
# RUN mkdir -pv /etc/nginx && \
#     cp -pv /usr/local/conf/* /etc/nginx/
#     # mkdir -pv /var/log/nginx 

# CMD /usr/local/sbin/nginx -c /etc/nginx/nginx.conf

