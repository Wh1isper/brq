FROM python:3.11.10-slim-bookworm as builder

RUN pip install hatch
COPY . /source
WORKDIR /source
RUN hatch build

FROM python:3.11.10-slim-bookworm

COPY --from=builder /source/dist/*.whl /tmp/

RUN pip install --no-cache-dir $(echo /tmp/*.whl)[browser]

LABEL org.opencontainers.image.source=https://github.com/b-scheduler/bscheduler
