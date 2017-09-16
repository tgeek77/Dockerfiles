FROM opensuse
RUN zypper --non-interactive in tar wget make gcc patch gcc-c++ python zip unzip mozilla-nspr-devel ncurses-devel
RUN mkdir sbbs
ADD sbbs_run.tgz /sbbs/
ADD sbbs_src.tgz /sbbs/
RUN ls /sbbs
#RUN cd /sbbs && tar -xzf sbbs_src.tgz; tar -xzf sbbs_run.tgz
RUN cd /sbbs/src/sbbs3/scfg make RELEASE=1 && cd /sbbs/src/sbbs3/scfg; make RELEASE=1
RUN cd /sbbs/xtrn/sbj; make && cd /sbbs/xtrn/sbl; make
RUN ln -s /sbbs/src/sbbs3/gcc.*.exe.release/* /sbbs/exec/. && ln -s /sbbs/src/sbbs3/scfg/gcc.*.exe.release/scfg* /sbbs/exec/.
RUN cd /sbbs/exec/; make

