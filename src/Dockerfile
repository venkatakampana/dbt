# Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
# SPDX-License-Identifier: MIT-0

FROM public.ecr.aws/i4u5z5o0/python-slim-buster:3.7.12

ADD dbt-project /dbt-project

# Update and install system packages
RUN apt-get update -y && \
  apt-get install --no-install-recommends -y -q \
  git libpq-dev python-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install DBT
RUN pip install -U pip
RUN pip install dbt-core dbt-postgres dbt-redshift dbt-snowflake dbt-bigquery
RUN cd /dbt-project && dbt deps

WORKDIR /dbt-project

