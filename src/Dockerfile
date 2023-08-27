# This seems to include 8.17.1   :-)
ARG COQ_IMAGE=coqorg/coq:8.17-ocaml-4.14-flambda
FROM ${COQ_IMAGE}

ARG OPAM_PACKAGES=coq-quickchick coq-equations.1.3+8.17

# Install opam packages
# QuickChick is pinned manually to a specific commit since 2.0 beta release is not on opam
# The last line is almost certainly not the correct way to get the
#    .opam/default link created
RUN opam update && \
    opam install -y -j ${NJOBS} ${OPAM_PACKAGES} && \
    opam clean -y -a -c -s --logs && \
    eval $(opam env) && \
    ln -s 4.14.1+flambda .opam/default
