FROM ubuntu:focal

# CIRCT
ENV PATH="/workspaces/Chisel/circt/build/bin:$PATH"
RUN \
  apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y cmake ninja-build clang && \
  mkdir -p "/root/.local/share/CMakeTools" && \
    echo '[{"name": "Clang 10", "compilers": {"C": "/bin/clang-10", "CXX": "/bin/clang++-10"}}]' \
      > "/root/.local/share/CMakeTools/cmake-tools-kits.json" 


# Chisel
# https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Linux.html
RUN \
  apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y curl gnupg && \
  (echo "deb https://repo.scala-sbt.org/scalasbt/debian all main" \ 
    | tee /etc/apt/sources.list.d/sbt.list) && \
  (echo "deb https://repo.scala-sbt.org/scalasbt/debian /" \
    | tee /etc/apt/sources.list.d/sbt_old.list) && \
  (curl -sL "https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x2EE0EA64E40A89B84B2DF73499E82A75642AC823" \
    | apt-key add) && \
  apt-get update && \ 
    DEBIAN_FRONTEND=noninteractive apt-get install -y scala sbt
