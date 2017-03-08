FROM opensuse
ADD supportutils-3.0-85.1.noarch.rpm /
RUN zypper --non-interactive in /supportutils-3.0-85.1.noarch.rpm
CMD /sbin/supportconfig -A -Q -R ~/
