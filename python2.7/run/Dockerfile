FROM lambci/lambda-base

ENV PATH=/usr/local/bin:/usr/bin/:/bin \
    LD_LIBRARY_PATH=/lib64:/usr/lib64:/var/runtime:/var/runtime/lib:/var/task:/var/task/lib \
    LANG=en_US.UTF-8 \
    AWS_EXECUTION_ENV=AWS_Lambda_python2.7 \
    PYTHONPATH=/var/runtime \
    LAMBDA_TASK_ROOT=/var/task \
    LAMBDA_RUNTIME_DIR=/var/runtime \
    _LAMBDA_CONTROL_SOCKET=14 \
    _LAMBDA_SHARED_MEM_FD=11 \
    _LAMBDA_LOG_FD=9 \
    _LAMBDA_CONSOLE_SOCKET=16 \
    _LAMBDA_RUNTIME_LOAD_TIME=1530232235231

RUN rm -rf /var/runtime /var/lang && mkdir /tmp && chown sbx_user1051:495 /tmp && chmod 700 /tmp && \
  curl https://lambci.s3.amazonaws.com/fs/python2.7.tgz | tar -zx -C /

RUN rm /var/runtime/awslambda/runtime.so
ADD runtime-mock.py /var/runtime/awslambda/runtime.py

WORKDIR /var/task

USER sbx_user1051

ENTRYPOINT ["/usr/bin/python2.7", "/var/runtime/awslambda/bootstrap.py"]
