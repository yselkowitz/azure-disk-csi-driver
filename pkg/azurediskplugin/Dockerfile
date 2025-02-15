# Copyright 2019 The Kubernetes Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM k8s.gcr.io/build-image/debian-base:bullseye-v1.0.0

RUN apt update && apt-mark unhold libcap2
RUN clean-install util-linux e2fsprogs mount ca-certificates udev xfsprogs btrfs-progs
# install updated packages to fix CVE issues
RUN clean-install libssl1.1 libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0

LABEL maintainers="andyzhangx"
LABEL description="Azure Disk CSI Driver"

ARG ARCH=amd64
ARG PLUGIN_NAME=azurediskplugin
COPY ./_output/${ARCH}/${PLUGIN_NAME} /azurediskplugin
ENTRYPOINT ["/azurediskplugin"]
