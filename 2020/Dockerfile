FROM ubuntu:18.04

RUN apt-get update; \
	apt-get install -y --no-install-recommends \
	ca-certificates \
	git \
	vim \
	perlbrew \
	perl-doc \
	patch \
	less \
	inetutils-ping \
	wget \
	curl \
	libssl-dev \
	postgresql \
	postgresql-server-dev-all \
	libmysqlclient-dev \
	mysql-client \
	mysql-server \
	redis \
	;

# Perl tools
RUN echo y | cpan -T App::cpanminus
RUN cpanm -n App::cpm
RUN cpanm -n local::lib
#RUN unset PERL5LIB; unset PERL_LOCAL_LIB_ROOT; eval $(perl -Mlocal::lib=./local)
RUN cpm install App::perlbrew

# Perl versions
RUN perlbrew init
RUN perlbrew install -j 5 --notest perl-5.16.3
RUN perlbrew install -j 5 --notest perl-5.26.3
RUN perlbrew install -j 5 --notest perl-5.33.4

RUN perlbrew switch perl-5.26.3

RUN cpanm -nf App::cpm
RUN cpanm -nf local::lib
