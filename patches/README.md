### gcc-*-ashrsi3-late-expanding.patch

A patch that changes processing of dynamic shift by a constant. First, it does not emit library call for ashrsi3 during expand pass. Instead it emits intermediate 'collapsed' libcall insn which is expanded later at split1 pass. Consecutive right arithmetic shifts can be catched at combine pass and converted to 'collapsed' libcall insn. Then 'collapsed' insn splits whether to short sequnce of individual right shifts or to `__ashiftrt_r4_N` library call during split1 pass. Finally, loop move invariants only pass executed right after split1 pass to hoist library addresses that potentially were emitted during split pass.

### Usage

#### gcc-*-ashrsi3-late-expanding.patch

No command line options needed.
