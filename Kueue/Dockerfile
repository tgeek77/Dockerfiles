
FROM opensuse
MAINTAINER Jason Evans <jevans@suse.com>

RUN zypper refresh 
RUN zypper --non-interactive in Mesa-libGL1 xorg-x11-fonts && zypper --non-interactive --no-gpg-checks in http://download.opensuse.org/repositories/home:/ntami:/kueue/openSUSE_Leap_42.2/x86_64/kueue-5.5.7-1.1.x86_64.rpm

ENV HOME /home/user
RUN useradd --create-home --home-dir $HOME user \
	&& chown -R user $HOME

ENV LANG C.UTF-8

# good fonts
COPY local.conf /etc/fonts/local.conf

WORKDIR $HOME
USER user

CMD [ "/usr/bin/kueue" ]
