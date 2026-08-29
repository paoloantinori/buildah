FROM alpine

# u+x,go-rwx on a plain (non-executable, 0644) source file: 0644 -> 0700
COPY --chmod=u+x,go-rwx copychmod.txt /tmp/sym1
# a+rX,go-w on an executable (0755) script: X keeps the exec bit, 0755
COPY --chmod=a+rX,go-w copysym.sh /tmp/sym2
# a+rX on a plain (non-executable, 0644) file: the conditional X adds
# nothing, the mode stays 0644
COPY --chmod=a+rX copychmod.txt /tmp/sym3

RUN stat -c "sym1:%a" /tmp/sym1
RUN stat -c "sym2:%a" /tmp/sym2
RUN stat -c "sym3:%a" /tmp/sym3
CMD /bin/sh
