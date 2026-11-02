# Survey: Heaven Dust (010059100D928000)

- display version: 1.0.2
- base: `Heaven Dust [UPDATE 1.0.2] [010059100d928000].nsp` (0.62 GB)

## Code modules

| module | what | build ID | text / ro / data (MB) | bss (MB) |
|---|---|---|---|---|
| main | the game | `865154d863bdab408aa124048ed015c1` | 28.4 / 13.8 / 2.7 | 3.2 |
| rtld | rtld | `31a2773ea6928ffe3d32b17b3ad08f54` | 0.0 / 0.0 / 0.0 | 0.0 |
| sdk | nnSdk | `ad3fdfbd62a5f4b082d385ffe420d440` | 5.2 / 6.3 / 6.4 | 0.7 |
| subsdk0 | NintendoSDK_movie | `5a7ada8dd7447c10aa244944f64d0aff` | 3.4 / 2.3 / 0.2 | 1.1 |

- main.npdm program ID: `010059100D928000`
- system resource: 16 MB
- SDK: 9_3_1 (Mario: 16_2_0 / 16_2_12)
- SDK components: NintendoSDK_NVN-9_3_1, NintendoSDK_libcurl-9_3_0, NintendoSDK_libz-9_3_1, NintendoSDK_movie-9_3_1, NintendoSdk_nnSdk-9_3_1
- Unity: 2019.2.15f1
- engine and API markers: NVN (main, sdk, subsdk0); Unity IL2CPP (main); Unity (main); FMOD (main)

## RomFS: 26 files, 0.59 GB

| top level | files | GB |
|---|---|---|
| Data | 16 | 0.58 |
| Data/StreamingAssets | 6 | 0.00 |
| Data/Managed | 2 | 0.00 |
| Data/Resources | 2 | 0.00 |

| header magic | files | GB |
|---|---|---|
| FMOD | 2 | 0.01 |

extensions: `(none)` 6, `.data` 6, `.ress` 5, `.assets` 4, `.dat` 2, `.resource` 2, `.config` 1

## Rewrite-site census (insn_census.py)

```
extract/ExeFS/main: 7450748 instructions decoded (138 undecodable words)
  x18 use                15851
extract/ExeFS/sdk: 1375583 instructions decoded (273 undecodable words)
  x18 use                11183
  svc                    61
  mrs tpidrro_el0        60
  mrs cntpct_el0         32
  msr tpidr_el0          3
  mrs tpidr_el0          2
  svc numbers: #1 x1, #2 x1, #3 x1, #4 x1, #5 x1, #6 x1, #7 x1, #8 x1, #9 x1, #0xa x1, #0xb x1, #0xc x1, #0xd x1, #0xe x1, #0xf x1, #0x10 x1, #0x11 x1, #0x12 x1, #0x13 x1, #0x14 x1, #0x15 x1, #0x16 x1, #0x17 x1, #0x18 x1, #0x19 x1, #0x1a x1, #0x1b x1, #0x1c x1, #0x1d x1, #0x1f x1, #0x21 x1, #0x22 x1, #0x23 x1, #0x25 x1, #0x26 x1, #0x27 x1, #0x28 x1, #0x29 x1, #0x2a x1, #0x2c x1, #0x2d x1, #0x2f x1, #0x32 x1, #0x33 x1, #0x34 x1, #0x35 x1, #0x36 x1, #0x40 x1, #0x41 x1, #0x43 x1, #0x44 x1, #0x45 x1, #0x48 x1, #0x49 x1, #0x4b x1, #0x50 x1, #0x51 x1, #0x52 x1, #0x53 x1, #0x70 x1, #0x72 x1
extract/ExeFS/subsdk0: 895350 instructions decoded (314 undecodable words)
  x18 use                10201
```

## Imports vs host hooks (nso_syms.py)

```
HLE hooks in host: 965 | present in new game sdk exports: 768
main imports: old game 0, new game 841, shared 0, new-only 841

new game main imports by area (total / not imported by old game):
  C / libc                 201 /  201
  nn::hid                  101 /  101
  nn::os                    79 /   79
  other C++                 71 /   71
  nn::friends               67 /   67
  nn::ec                    63 /   63
  nn::audio                 45 /   45
  nn::fs                    39 /   39
  nn::socket                29 /   29
  nn::account               26 /   26
  nn::irsensor              24 /   24
  nn::swkbd                 24 /   24
  nn::oe                    15 /   15
  nn::nifm                   9 /    9
  nn::ssl                    6 /    6
  nn::mem                    6 /    6
  nn::err                    6 /    6
  nn::ngc                    5 /    5
  nn::time                   5 /    5
  nn::vi                     4 /    4
  nn::aoc                    3 /    3
  nn::pl                     3 /    3
  nn::cstd                   2 /    2
  nn::util                   2 /    2
  nn::diag                   2 /    2
  nn::crypto                 1 /    1
  nvn                        1 /    1
  nn::nsd                    1 /    1
  nn::settings               1 /    1

examples of new-only imports per area:
  C / libc: _Unwind_Resume, __assert_fail, __cxa_allocate_exception, __cxa_begin_catch
  nn::hid: _ZN2nn3hid12GetNpadStateEPNS0_16NpadFullKeyStateERKj, _ZN2nn3hid12GetNpadStateEPNS0_16NpadJoyDualStateERKj, _ZN2nn3hid12GetNpadStateEPNS0_16NpadJoyLeftStateERKj, _ZN2nn3hid12GetNpadStateEPNS0_17NpadHandheldStateERKj
  nn::os: _ZN2nn2os10ClearEventEPNS0_9EventTypeE, _ZN2nn2os10WaitThreadEPNS0_10ThreadTypeE, _ZN2nn2os11FreeTlsSlotENS0_7TlsSlotE, _ZN2nn2os11GetHostArgcEv
  other C++: _ZN2nv18InitializeGraphicsEPvm, _ZN2nv20SetGraphicsAllocatorEPFPvmmS0_EPFvS0_S0_EPFS0_S0_mS0_ES0_, _ZN2nv28SetGraphicsDevtoolsAllocatorEPFPvmmS0_EPFvS0_S0_EPFS0_S0_mS0_ES0_, _ZN5movie11SetCoreMaskEm
  nn::friends: _ZN2nn7friends10InitializeEv, _ZN2nn7friends12AsyncContext6CancelEv, _ZN2nn7friends12AsyncContext7HasDoneEPb, _ZN2nn7friends12AsyncContextC1Ev
  nn::ec: _ZN2nn2ec19ShopServiceAccessor10InitializeERKNS0_11ShopServiceE, _ZN2nn2ec19ShopServiceAccessor13AsyncResponse3GetEPvm, _ZN2nn2ec19ShopServiceAccessor13AsyncResponse4WaitEv, _ZN2nn2ec19ShopServiceAccessor13AsyncResponse6CancelEv
  nn::audio: _ZN2nn5audio12StopAudioOutEPNS0_8AudioOutE, _ZN2nn5audio13AddDeviceSinkEPNS0_19AudioRendererConfigEPNS0_14DeviceSinkTypeEPNS0_12FinalMixTypeEPKaiPKc, _ZN2nn5audio13CloseAudioOutEPNS0_8AudioOutE, _ZN2nn5audio13ListAudioOutsEPNS0_12AudioOutInfoEi
  nn::fs: _ZN2nn2fs10CreateFileEPKcl, _ZN2nn2fs10DeleteFileEPKc, _ZN2nn2fs10RenameFileEPKcS2_, _ZN2nn2fs11GetFileSizeEPlNS0_10FileHandleE
  nn::socket: _ZN2nn6socket10InitializeEPvmmi, _ZN2nn6socket10InitializeERKNS0_6ConfigE, _ZN2nn6socket10SetSockOptEiiiPKvj, _ZN2nn6socket11GAIStrErrorEi
  nn::account: _ZN2nn7account10InitializeEv, _ZN2nn7account11GetNicknameEPNS0_8NicknameERKNS0_3UidE, _ZN2nn7account12AsyncContext6CancelEv, _ZN2nn7account12AsyncContext7HasDoneEPb
  nn::irsensor: _ZN2nn8irsensor10InitializeERKNS0_14IrCameraHandleE, _ZN2nn8irsensor15RunHandAnalysisERKNS0_14IrCameraHandleERKNS0_18HandAnalysisConfigE, _ZN2nn8irsensor17GetIrCameraHandleERKj, _ZN2nn8irsensor17GetIrCameraStatusERKNS0_14IrCameraHandleE
  nn::swkbd: _ZN2nn5swkbd10MakePresetEPNS0_14KeyboardConfigENS0_6PresetE, _ZN2nn5swkbd10SetSubTextEPNS0_14KeyboardConfigEPKDs, _ZN2nn5swkbd12SetGuideTextEPNS0_14KeyboardConfigEPKDs, _ZN2nn5swkbd12ShowKeyboardEPNS0_6StringERKNS0_15ShowKeyboardArgE
  nn::oe: _ZN2nn2oe16GetOperationModeEv, _ZN2nn2oe17EnableCrashReportEv, _ZN2nn2oe18DisableCrashReportEv, _ZN2nn2oe18GetDesiredLanguageEv
  nn::nifm: _ZN2nn4nifm10InitializeEv, _ZN2nn4nifm18IsNetworkAvailableEv, _ZN2nn4nifm19SetLocalNetworkModeEb, _ZN2nn4nifm20CancelNetworkRequestEv
```

## What it means for a port

- modules besides main / sdk: subsdk0 (NintendoSDK_movie); the provisional profile loads main subsdk0 sdk (load order main, subsdk*, sdk)
- Unity: the shaders are Shader objects in UnityFS bundles and data.unity3d, which shader_split.py reads through unityfs.py (written for Unity 2020.3's Switch format, also read for 2017.4, 2018.3, 2022.3 and 6000.0; check other Unity versions first)
- main has 5 GLSLC compiler output magics (0x19866891): shader_split.py takes those that are whole outputs (13 Sentinels and the KTGL games compile their shaders into main; Unity's player has 11 of its own)
- SDK 9, not Mario's 16: NVN object sizes, API version and service layouts differ by SDK (the host was converted from D2R's SDK 12 to SDK 16 sizes); check them one by one per docs/agents/03

## Provisional profile keys (dm/games/profile_guess.py)

What the game files decide; mem_used follows the rewrite, and a game with virtual address memory that sets a heap gets a heap check on the Mac (scripts/build_ipa_from_nsp.py heap_check).

```
modules	main subsdk0 sdk	# every module main imports from
mem_reserve	0x140000000	# the NPDM declares 16 MB of system resource (virtual address memory) and main sets a heap: a 5 GB block with a large alias region; the heap check sizes the heap region from the heap the game asks for
mem_alias	0x118000000
mem_stack	0x10000000
app_pool	0xCD500000
sys_resource	0x1000000	# the NPDM declares 16 MB of system resource
```

Next steps: docs/agents (02 survey, 03 bring-up).
