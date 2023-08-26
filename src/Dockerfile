ARG COQ_IMAGE=coqorg/coq:8.17-ocaml-4.14-flambda
FROM ${COQ_IMAGE}

ARG OPAM_PACKAGES=coq-equations.1.3+8.17

# Install opam packages
# QuickChick is pinned manually to a specific commit since 2.0 beta release is not on opam
RUN opam install -y -j ${NJOBS} ${OPAM_PACKAGES} && \
    opam pin -y -j ${NJOBS} add https://github.com/QuickChick/QuickChick.git#9b9207ff9334b3b26a1f20537b4cf8e48e04fd58 && \
    opam clean -y -a -c -s --logs && \
    eval $(opam env)
