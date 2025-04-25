
> [!NOTE]
> 
> Useful information that users should know, even when skimming content.
> 
> [!TIP]
> 
> Helpful advice for doing things better or more easily.

[!IMPORTANT]

Key information users need to know to achieve their goal.

[!WARNING]

Urgent info that needs immediate user attention to avoid problems.

[!CAUTION]

Advises about risks or negative outcomes of certain actions.


# OpenHarmony_sig组织PR评论支持命令清单
sig仓库门禁    
触发方式从之前的被动触发变为主动触发，需要评论内容“sig start build”     
合并方式      
代码审查需要管理员点击审查进行完成。（重要，不要点击全部测试完成。管理员确认代码侯只点击审核即可）  
代码测试需要待dco检测，合规检测，代码质量检测，三个检测完成后。门禁会通过测试，  
提交PR待审查人员点击确认审查后会自动进行合并。  

其中编译命令如下：


| 评论输入命令        | 是否必选          | 使用场景                                                     | 命令触发角色 |
| ------------------ | ---------------- | ------------------------------------------------------------ | ------------ |
| sig start build    | 必选             |首次提交PR时，评论sig start build进行触发检查                   |仓库管理员/PR提交者
| check dco          | 可选             | DCO检查失败时, 更新DCO信息后,人工触发检查DCO<br>检查通过条件:gitee账户邮箱已签署DCO+PR所有提交均包含Signed-off-by信息，检查通过 | 仓库管理员/PR提交者     |
| codecheck          | 可选             | 合规检查失败时, 更新合规信息后,人工触发代码合规检查测试                           |  仓库管理员/PR提交者       |
| qualitycheck       | 可选             | 代码质量检测失败时, 按照评论修改, 人工触发代码质量测试                             |  仓库管理员/PR提交者        |
| build              | 可选             | 进行编译检查（需要先和管理员确认配置过编译门禁）                      | 任何人        |
| no check dco       | 可选             | 引入第三方信息时，若其中包含无DCO信息，可使用此命令，跳过DCO检测，操作人需要对此次操作负责 | openharmony_sig_ci   |
| submit             | 可选             | 当PR各项检测通过，且opengharmony_sig_ci和仓库管理员分别测试和审查通过后，可以评论submit进行合入 |仓库管理员/PR提交者|



# OpenHarmony_sig组织仓库规则说明
1.仓库不允许在线编辑文档；  
2.仓库不允许任何人推送代码；  
3.关闭WEB界面PR合并权限       
4.设置仓库所有分支为保护分支；  
5.指派审查为仓库管理员，指派测试为openharmony_sig_ci,PR通过测试和管理员审查后会自动合并，仓库管理员只能进行审查操作，不能进行测试操作，测试操作只能为openharmony_sig_ci；  
6.开发者提交PR后，需要在PR下评论'sig start build'才能触发仓库门禁检查，sig start build指令会同时触发check dco、codecheck、qualitycheck检查，当需要进行其中一项检查时， 可以评论对应的命令进行单独触发检查；    


# OpenHarmony_sig组织仓库门禁规则说明
1.门禁将对PR进行DCO检测，代码合规检测，代码质量检测以及代码编译检测,结果将在此次PR打上对应标签。  
2.PR不涉及代码改动时，将不进行代码质量检测与代码编译检测。  
3.代码合规检测，检测所有代码文件受否加入许可头以及版权头，检查代码文件是否有许可和版权篡改风险，检查仓库根目录下是否含有LICENSE（能让gitee正常识别到），若没有会检测pr中是否有/LICENSE，没有则检测失败。若对结果有异议可以联系管理员确认问题。  
4.代码质量检测会对代码改动进行质量测试，目前支持的语言为   
C++，java，JavaScript，Python，PHP，CSS，HTML，Go，TypeScript，C#  
5.DCO审核不过，不允许合并（check dco二次审核）  
6.合规扫描不过，不允许合并（codecheck 二次审核）  
7.质量扫描不过，不允许合并（qualitycheck 二次审核）  
8.编译不通过不允许合并 （build 二次编译）（需要先联系仓库管理员确认和配置相关编译工作）  
9.每次提pr，自动触发合并流程（顺序执行检查），DCO与合规检查完成后自动合并  
10.管理员需要对仓库负责，做好审查测试的工作，合并PR需要确认再操作，操作者会对操作负责。


# OpenHarmony_sig门禁联系方式
若对sig组织门禁检测结果有异议或有特殊情况需要声明，可联系仓库管理员，或可订阅Zulip的[openharmony-sig-ci](https://zulip.openharmony.cn/#narrow/stream/52-OpenHarmony-SIG-CICD/topic/stream.20events/near/5586)或我们将及时给您回复相关疑问的解答。  


# OpenHarmony_sig组织仓库情况
| 仓库名称 | 管理员信息 |                          仓库简介                             |  issue数量  |  PR数量  |  开启PR数量  |  关闭PR数量  |  合并PR数量  |
| -------- | ---------- | ------------------------------------------------------------ | ---------- | -------- |   --------  |   --------  |   --------  |
| [app-samples](https://gitee.com/openharmony-sig/app-samples.git) | [liuguo](https://gitee.com/guoguoliu),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) | The Reference Implementation SIG maintains and evolves the creative idea and the implementation of the concrete devices powered by OpenHarmony. | [0](https://gitee.com/openharmony-sig/app-samples/issues) | [0](https://gitee.com/openharmony-sig/app-samples/pulls) | 0 |0 |0 | 
| [SIG-Tools-Toolchains](https://gitee.com/openharmony-sig/sig-tools-toolchains.git) | [mamingshuai](https://gitee.com/landwind),[Bernhard Rosenkraenzer](https://gitee.com/berolinux),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/sig-tools-toolchains/issues) | [0](https://gitee.com/openharmony-sig/sig-tools-toolchains/pulls) | 0 |0 |0 | 
| [SIG-Open-Source-RTOS](https://gitee.com/openharmony-sig/sig-open-source-rtos.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/sig-open-source-rtos/issues) | [0](https://gitee.com/openharmony-sig/sig-open-source-rtos/pulls) | 0 |0 |0 | 
| [SIG-OTA-Updates](https://gitee.com/openharmony-sig/sig-ota-updates.git) | [mamingshuai](https://gitee.com/landwind),[Andrei Gherzan](https://gitee.com/agherzan),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/sig-ota-updates/issues) | [0](https://gitee.com/openharmony-sig/sig-ota-updates/pulls) | 0 |0 |0 | 
| [SIG-reST-Sphynx](https://gitee.com/openharmony-sig/sig-re-st-sphynx.git) | [mamingshuai](https://gitee.com/landwind),[Ratna Kishore](https://gitee.com/ratnakishore),[sgururajshetty](https://gitee.com/gururajshetty),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/sig-re-st-sphynx/issues) | [8](https://gitee.com/openharmony-sig/sig-re-st-sphynx/pulls) | 1 |6 |1 | 
| [device_st](https://gitee.com/openharmony-sig/device_st.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[Denny](https://gitee.com/DennyShen),[zianed](https://gitee.com/zianed),[zeeman](https://gitee.com/zeeman_wang),[wanchengzhen](https://gitee.com/wanchengzhen),[borne](https://gitee.com/borne),[Caoruihong](https://gitee.com/caoruihong),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[Laowang-BearPi](https://gitee.com/laowang-bearpi) |  | [0](https://gitee.com/openharmony-sig/device_st/issues) | [10](https://gitee.com/openharmony-sig/device_st/pulls) | 0 |4 |6 | 
| [vendor_huawei_minidisplay_demo](https://gitee.com/openharmony-sig/vendor_huawei_minidisplay_demo.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[Denny](https://gitee.com/DennyShen),[zianed](https://gitee.com/zianed),[zeeman](https://gitee.com/zeeman_wang),[wanchengzhen](https://gitee.com/wanchengzhen),[borne](https://gitee.com/borne),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_huawei_minidisplay_demo/issues) | [7](https://gitee.com/openharmony-sig/vendor_huawei_minidisplay_demo/pulls) | 2 |2 |3 | 
| [manifest](https://gitee.com/openharmony-sig/manifest.git) | [mamingshuai](https://gitee.com/landwind),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) | 统一管理各sig组的代码 | [1](https://gitee.com/openharmony-sig/manifest/issues) | [80](https://gitee.com/openharmony-sig/manifest/pulls) | 0 |25 |55 | 
| [oh-inner-release-management](https://gitee.com/openharmony-sig/oh-inner-release-management.git) | [jinguang](https://gitee.com/dongjinguang),[aiyongfu](https://gitee.com/aiyongfu),[frank_bing](https://gitee.com/libing_frank),[张磊](https://gitee.com/zhanglei179),[yexiangbin](https://gitee.com/ye-xiangbin),[jiyong](https://gitee.com/jiyong_sd),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[聂欣](https://gitee.com/nie-x) | 1、需求：内部转测试的双周非正式版本信息承载<br />2、目标：OH非正式版本的信息承载<br />3、意义：非官方开发转测试通道<br /> | [2](https://gitee.com/openharmony-sig/oh-inner-release-management/issues) | [416](https://gitee.com/openharmony-sig/oh-inner-release-management/pulls) | 7 |138 |271 | 
| [device_allwinner](https://gitee.com/openharmony-sig/device_allwinner.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[duxbbo](https://gitee.com/dxbedu),[Denny](https://gitee.com/DennyShen),[zianed](https://gitee.com/zianed),[wanchengzhen](https://gitee.com/wanchengzhen),[borne](https://gitee.com/borne),[wangmihu](https://gitee.com/wangmihu2008),[bruce.cai](https://gitee.com/bruce-caijun),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[uncleli](https://gitee.com/moldy-potato-chips),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_allwinner/issues) | [13](https://gitee.com/openharmony-sig/device_allwinner/pulls) | 1 |3 |9 | 
| [vendor_huawei_ipcamera_v3s](https://gitee.com/openharmony-sig/vendor_huawei_ipcamera_v3s.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[Denny](https://gitee.com/DennyShen),[zianed](https://gitee.com/zianed),[wanchengzhen](https://gitee.com/wanchengzhen),[borne](https://gitee.com/borne),[wangmihu](https://gitee.com/wangmihu2008),[duxbbo](https://gitee.com/dxbedu),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_huawei_ipcamera_v3s/issues) | [9](https://gitee.com/openharmony-sig/vendor_huawei_ipcamera_v3s/pulls) | 0 |3 |6 | 
| [vendor_oh_fun](https://gitee.com/openharmony-sig/vendor_oh_fun.git) | [mamingshuai](https://gitee.com/landwind),[zeeman](https://gitee.com/zeeman_wang),[张前福](https://gitee.com/Cruise2021),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) | 基于OpenHarmony开源代码和开发板，打造一系列“ 趣味性、低门槛、成就感 ”的开源项目， 助你重新燃起心中的极客梦想之火！ | [18](https://gitee.com/openharmony-sig/vendor_oh_fun/issues) | [70](https://gitee.com/openharmony-sig/vendor_oh_fun/pulls) | 0 |22 |48 | 
| [tools_oat](https://gitee.com/openharmony-sig/tools_oat.git) | [mamingshuai](https://gitee.com/landwind),[jalenchen](https://gitee.com/jalenchen),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) | Scanning the license and copyright information of the open source repository <br /> 扫描开源仓许可证及版权信息 | [9](https://gitee.com/openharmony-sig/tools_oat/issues) | [29](https://gitee.com/openharmony-sig/tools_oat/pulls) | 0 |1 |28 | 
| [dllite_micro](https://gitee.com/openharmony-sig/dllite_micro.git) | [mamingshuai](https://gitee.com/landwind),[ArmyLee0](https://gitee.com/armylee0),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) | 为了支持AI模型在IoT设备上完成推理功能，使IoT设备具备AI能力，并能够更好的匹配OpenHarmonyOS的各种设备形态，DLLite SIG不仅需要为用户提供基础的推理服务，包括统一的API和 | [4](https://gitee.com/openharmony-sig/dllite_micro/issues) | [14](https://gitee.com/openharmony-sig/dllite_micro/pulls) | 0 |7 |7 | 
| [openblock](https://gitee.com/openharmony-sig/openblock.git) | [mamingshuai](https://gitee.com/landwind),[杜天微](https://gitee.com/duzc2),[胡天麒](https://gitee.com/htq110219891),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) | 为搭载OpenHarmony的设备提供统一、强大的图形化编程IDE<br />支持OpenHarmony的分布式特性<br />面向青少年，提供基础教育公共基础设施<br />提供基于H5的编译器，不再需要本地编译器<br />高效的编程语 | [1](https://gitee.com/openharmony-sig/openblock/issues) | [5](https://gitee.com/openharmony-sig/openblock/pulls) | 1 |1 |3 | 
| [openblock_blocks](https://gitee.com/openharmony-sig/openblock_blocks.git) | [mamingshuai](https://gitee.com/landwind),[杜天微](https://gitee.com/duzc2),[胡天麒](https://gitee.com/htq110219891),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/openblock_blocks/issues) | [0](https://gitee.com/openharmony-sig/openblock_blocks/pulls) | 0 |0 |0 | 
| [devboard](https://gitee.com/openharmony-sig/devboard.git) | [mamingshuai](https://gitee.com/landwind),[刘洋](https://gitee.com/liuyang198591),[Leon](https://gitee.com/jahyeon),[赵秀秀](https://gitee.com/zhao_xiuxiu),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code) | 为了增加OpenHarmony OS所支持的三方单板数量，Device SIG不仅需要提高系统的易移植性，包括内核和编译构建系统的易移植性需求， 提供三方单板移植手册，创建移植样例工程；更为重要的是， | [10](https://gitee.com/openharmony-sig/devboard/issues) | [3](https://gitee.com/openharmony-sig/devboard/pulls) | 1 |2 |0 | 
| [device_mediatek](https://gitee.com/openharmony-sig/device_mediatek.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_mediatek/issues) | [0](https://gitee.com/openharmony-sig/device_mediatek/pulls) | 0 |0 |0 | 
| [device_nordic](https://gitee.com/openharmony-sig/device_nordic.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_nordic/issues) | [0](https://gitee.com/openharmony-sig/device_nordic/pulls) | 0 |0 |0 | 
| [device_nxp](https://gitee.com/openharmony-sig/device_nxp.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_nxp/issues) | [0](https://gitee.com/openharmony-sig/device_nxp/pulls) | 0 |0 |0 | 
| [device_fudanmicro](https://gitee.com/openharmony-sig/device_fudanmicro.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_fudanmicro/issues) | [0](https://gitee.com/openharmony-sig/device_fudanmicro/pulls) | 0 |0 |0 | 
| [device_bestechnic](https://gitee.com/openharmony-sig/device_bestechnic.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[niulihua](https://gitee.com/niulihua),[antslink](https://gitee.com/hongdaozi),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [8](https://gitee.com/openharmony-sig/device_bestechnic/issues) | [92](https://gitee.com/openharmony-sig/device_bestechnic/pulls) | 0 |26 |66 | 
| [device_ingenic](https://gitee.com/openharmony-sig/device_ingenic.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[bruce.cai](https://gitee.com/bruce-caijun),[dsqiu](https://gitee.com/dsqiu),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_ingenic/issues) | [25](https://gitee.com/openharmony-sig/device_ingenic/pulls) | 0 |7 |18 | 
| [device_espressif](https://gitee.com/openharmony-sig/device_espressif.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_espressif/issues) | [2](https://gitee.com/openharmony-sig/device_espressif/pulls) | 1 |1 |0 | 
| [device_winnermicro](https://gitee.com/openharmony-sig/device_winnermicro.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_winnermicro/issues) | [1](https://gitee.com/openharmony-sig/device_winnermicro/pulls) | 0 |1 |0 | 
| [device_unisoc](https://gitee.com/openharmony-sig/device_unisoc.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_unisoc/issues) | [0](https://gitee.com/openharmony-sig/device_unisoc/pulls) | 0 |0 |0 | 
| [device_broadcom](https://gitee.com/openharmony-sig/device_broadcom.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_broadcom/issues) | [0](https://gitee.com/openharmony-sig/device_broadcom/pulls) | 0 |0 |0 | 
| [device_realtek](https://gitee.com/openharmony-sig/device_realtek.git) | [mamingshuai](https://gitee.com/landwind),[duxbbo](https://gitee.com/dxbedu),[zeeman](https://gitee.com/zeeman_wang),[jady3356](https://gitee.com/taiyipei),[borne](https://gitee.com/borne),[SimonLi](https://gitee.com/kkup180),[zianed](https://gitee.com/zianed),[Denny](https://gitee.com/DennyShen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_realtek/issues) | [2](https://gitee.com/openharmony-sig/device_realtek/pulls) | 0 |1 |1 | 
| [riscv](https://gitee.com/openharmony-sig/riscv.git) | [mamingshuai](https://gitee.com/landwind),[于佳耕](https://gitee.com/yu_jia_geng),[qwer](https://gitee.com/kevenNO1),[tayloryoung](https://gitee.com/iscas-taiyang_admin),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code) | RISC-V 是一个免费开源的指令集（ISA）。围绕RISC-V的软硬件生态都在快速完善。 RISC-V SIG 组旨在构建围绕OpenHarmony的软硬件生态，提供RISC-V的软件包和系统构建等 | [15](https://gitee.com/openharmony-sig/riscv/issues) | [11](https://gitee.com/openharmony-sig/riscv/pulls) | 0 |4 |7 | 
| [system_applications](https://gitee.com/openharmony-sig/system_applications.git) | [mamingshuai](https://gitee.com/landwind),[NicolasWang](https://gitee.com/nicolaswang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code) | 定义并构建OpenHarmony的系统应用，负责申请、实施孵化项目，广泛收集社区开发者需求，以持续完善系统应用的特性。 | [1](https://gitee.com/openharmony-sig/system_applications/issues) | [1](https://gitee.com/openharmony-sig/system_applications/pulls) | 0 |0 |1 | 
| [sig-content](https://gitee.com/openharmony-sig/sig-content.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[mamingshuai](https://gitee.com/landwind),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) | 为SIG仓提供文档、会议纪要及其他文档提供仓库，同时作为各SIG组的索引页 | [2](https://gitee.com/openharmony-sig/sig-content/issues) | [78](https://gitee.com/openharmony-sig/sig-content/pulls) | 0 |21 |57 | 
| [website](https://gitee.com/openharmony-sig/website.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[jinguang](https://gitee.com/dongjinguang),[liuguo](https://gitee.com/guoguoliu),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[xzmu](https://gitee.com/xzmu),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[ChangweiXu](https://gitee.com/changweixu) | OpenHarmony 官网源码 | [8](https://gitee.com/openharmony-sig/website/issues) | [6](https://gitee.com/openharmony-sig/website/pulls) | 1 |1 |4 | 
| [python](https://gitee.com/openharmony-sig/python.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[唐佐林](https://gitee.com/delphi-tang) |  | [2](https://gitee.com/openharmony-sig/python/issues) | [31](https://gitee.com/openharmony-sig/python/pulls) | 1 |25 |5 | 
| [cicd](https://gitee.com/openharmony-sig/cicd.git) | [mamingshuai](https://gitee.com/landwind),[xzmu](https://gitee.com/xzmu),[youthdragon](https://gitee.com/youthdragon),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) | OpenHarmony CICD 门禁平台 SIG | [1](https://gitee.com/openharmony-sig/cicd/issues) | [0](https://gitee.com/openharmony-sig/cicd/pulls) | 0 |0 |0 | 
| [linkboy](https://gitee.com/openharmony-sig/linkboy.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) | linkboy | [3](https://gitee.com/openharmony-sig/linkboy/issues) | [10](https://gitee.com/openharmony-sig/linkboy/pulls) | 0 |6 |4 | 
| [archive](https://gitee.com/openharmony-sig/archive.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[xzmu](https://gitee.com/xzmu),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) | 基础设施SIG组下 下属文档子SIG， 目前范围为 SIG仓、 官网website仓， community仓，以及其他的涉及社区知识体系的代码、文档仓等整理 | [1](https://gitee.com/openharmony-sig/archive/issues) | [0](https://gitee.com/openharmony-sig/archive/pulls) | 0 |0 |0 | 
| [device_beken](https://gitee.com/openharmony-sig/device_beken.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[bruce.cai](https://gitee.com/bruce-caijun),[SimonLi](https://gitee.com/kkup180),[xxkit](https://gitee.com/xxkit) | device_beken | [0](https://gitee.com/openharmony-sig/device_beken/issues) | [6](https://gitee.com/openharmony-sig/device_beken/pulls) | 1 |2 |3 | 
| [devboard_device_hihope_build](https://gitee.com/openharmony-sig/devboard_device_hihope_build.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[mamingshuai](https://gitee.com/landwind),[jony](https://gitee.com/jony_code) | 润和代码仓 | [2](https://gitee.com/openharmony-sig/devboard_device_hihope_build/issues) | [19](https://gitee.com/openharmony-sig/devboard_device_hihope_build/pulls) | 0 |13 |6 | 
| [devboard_device_hihope_dayu](https://gitee.com/openharmony-sig/devboard_device_hihope_dayu.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[mamingshuai](https://gitee.com/landwind),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/devboard_device_hihope_dayu/issues) | [7](https://gitee.com/openharmony-sig/devboard_device_hihope_dayu/pulls) | 0 |5 |2 | 
| [devboard_vendor_hihope](https://gitee.com/openharmony-sig/devboard_vendor_hihope.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code) |  | [1](https://gitee.com/openharmony-sig/devboard_vendor_hihope/issues) | [3](https://gitee.com/openharmony-sig/devboard_vendor_hihope/pulls) | 0 |1 |2 | 
| [third_party_llvm-project](https://gitee.com/openharmony-sig/third_party_llvm-project.git) | [mamingshuai](https://gitee.com/landwind),[zhuoli72](https://gitee.com/zhuoli72),[openharmony_ci](https://gitee.com/openharmony_ci),[hhj](https://gitee.com/huanghuijin),[dhy308](https://gitee.com/dhy308),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [1](https://gitee.com/openharmony-sig/third_party_llvm-project/issues) | [1](https://gitee.com/openharmony-sig/third_party_llvm-project/pulls) | 0 |0 |1 | 
| [third_party_lldb-mi](https://gitee.com/openharmony-sig/third_party_lldb-mi.git) | [mamingshuai](https://gitee.com/landwind),[zhuoli72](https://gitee.com/zhuoli72),[openharmony_ci](https://gitee.com/openharmony_ci),[hhj](https://gitee.com/huanghuijin),[dhy308](https://gitee.com/dhy308),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/third_party_lldb-mi/issues) | [1](https://gitee.com/openharmony-sig/third_party_lldb-mi/pulls) | 0 |0 |1 | 
| [resourceschedule_workscheduler](https://gitee.com/openharmony-sig/resourceschedule_workscheduler.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhaofanfan](https://gitee.com/FrankJone),[hujun211](https://gitee.com/hujun211),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/resourceschedule_workscheduler/issues) | [0](https://gitee.com/openharmony-sig/resourceschedule_workscheduler/pulls) | 0 |0 |0 | 
| [resourceschedule_backgroundtaskmanager](https://gitee.com/openharmony-sig/resourceschedule_backgroundtaskmanager.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhaofanfan](https://gitee.com/FrankJone),[hujun211](https://gitee.com/hujun211),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/resourceschedule_backgroundtaskmanager/issues) | [0](https://gitee.com/openharmony-sig/resourceschedule_backgroundtaskmanager/pulls) | 0 |0 |0 | 
| [applications_sample_bearpi_hm_nano](https://gitee.com/openharmony-sig/applications_sample_bearpi_hm_nano.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/applications_sample_bearpi_hm_nano/issues) | [4](https://gitee.com/openharmony-sig/applications_sample_bearpi_hm_nano/pulls) | 0 |2 |2 | 
| [device_bouffalolab](https://gitee.com/openharmony-sig/device_bouffalolab.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[bruce.cai](https://gitee.com/bruce-caijun),[Denny](https://gitee.com/DennyShen),[zianed](https://gitee.com/zianed),[SimonLi](https://gitee.com/kkup180),[borne](https://gitee.com/borne),[jady3356](https://gitee.com/taiyipei),[zeeman](https://gitee.com/zeeman_wang),[duxbbo](https://gitee.com/dxbedu),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_bouffalolab/issues) | [5](https://gitee.com/openharmony-sig/device_bouffalolab/pulls) | 0 |2 |3 | 
| [device_asrmicro](https://gitee.com/openharmony-sig/device_asrmicro.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_asrmicro/issues) | [0](https://gitee.com/openharmony-sig/device_asrmicro/pulls) | 0 |0 |0 | 
| [security_block_chain](https://gitee.com/openharmony-sig/security_block_chain.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/security_block_chain/issues) | [4](https://gitee.com/openharmony-sig/security_block_chain/pulls) | 0 |3 |1 | 
| [vendor_allwinner](https://gitee.com/openharmony-sig/vendor_allwinner.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[bruce.cai](https://gitee.com/bruce-caijun),[uncleli](https://gitee.com/moldy-potato-chips),[JetCui](https://gitee.com/jetcui),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_allwinner/issues) | [1](https://gitee.com/openharmony-sig/vendor_allwinner/pulls) | 0 |1 |0 | 
| [vendor_asrmicro](https://gitee.com/openharmony-sig/vendor_asrmicro.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_asrmicro/issues) | [0](https://gitee.com/openharmony-sig/vendor_asrmicro/pulls) | 0 |0 |0 | 
| [vendor_beken](https://gitee.com/openharmony-sig/vendor_beken.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[bruce.cai](https://gitee.com/bruce-caijun),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[xxkit](https://gitee.com/xxkit) |  | [0](https://gitee.com/openharmony-sig/vendor_beken/issues) | [2](https://gitee.com/openharmony-sig/vendor_beken/pulls) | 0 |1 |1 | 
| [vendor_bestechnic](https://gitee.com/openharmony-sig/vendor_bestechnic.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) | 基于恒玄芯片开发的轻量带屏显示产品样例代码 | [3](https://gitee.com/openharmony-sig/vendor_bestechnic/issues) | [98](https://gitee.com/openharmony-sig/vendor_bestechnic/pulls) | 0 |23 |75 | 
| [vendor_bouffalolab](https://gitee.com/openharmony-sig/vendor_bouffalolab.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[bruce.cai](https://gitee.com/bruce-caijun),[apzhao](https://gitee.com/apzhao),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_bouffalolab/issues) | [0](https://gitee.com/openharmony-sig/vendor_bouffalolab/pulls) | 0 |0 |0 | 
| [vendor_broadcom](https://gitee.com/openharmony-sig/vendor_broadcom.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_broadcom/issues) | [0](https://gitee.com/openharmony-sig/vendor_broadcom/pulls) | 0 |0 |0 | 
| [vendor_espressif](https://gitee.com/openharmony-sig/vendor_espressif.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_espressif/issues) | [2](https://gitee.com/openharmony-sig/vendor_espressif/pulls) | 1 |1 |0 | 
| [vendor_fudanmicro](https://gitee.com/openharmony-sig/vendor_fudanmicro.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_fudanmicro/issues) | [0](https://gitee.com/openharmony-sig/vendor_fudanmicro/pulls) | 0 |0 |0 | 
| [vendor_ingenic](https://gitee.com/openharmony-sig/vendor_ingenic.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[bruce.cai](https://gitee.com/bruce-caijun),[dsqiu](https://gitee.com/dsqiu),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_ingenic/issues) | [47](https://gitee.com/openharmony-sig/vendor_ingenic/pulls) | 0 |20 |27 | 
| [vendor_mediatek](https://gitee.com/openharmony-sig/vendor_mediatek.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_mediatek/issues) | [0](https://gitee.com/openharmony-sig/vendor_mediatek/pulls) | 0 |0 |0 | 
| [vendor_nordic](https://gitee.com/openharmony-sig/vendor_nordic.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_nordic/issues) | [0](https://gitee.com/openharmony-sig/vendor_nordic/pulls) | 0 |0 |0 | 
| [vendor_nxp](https://gitee.com/openharmony-sig/vendor_nxp.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_nxp/issues) | [0](https://gitee.com/openharmony-sig/vendor_nxp/pulls) | 0 |0 |0 | 
| [vendor_realtek](https://gitee.com/openharmony-sig/vendor_realtek.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_realtek/issues) | [0](https://gitee.com/openharmony-sig/vendor_realtek/pulls) | 0 |0 |0 | 
| [vendor_st](https://gitee.com/openharmony-sig/vendor_st.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_st/issues) | [0](https://gitee.com/openharmony-sig/vendor_st/pulls) | 0 |0 |0 | 
| [vendor_unisoc](https://gitee.com/openharmony-sig/vendor_unisoc.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_unisoc/issues) | [0](https://gitee.com/openharmony-sig/vendor_unisoc/pulls) | 0 |0 |0 | 
| [vendor_winnermicro](https://gitee.com/openharmony-sig/vendor_winnermicro.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_winnermicro/issues) | [7](https://gitee.com/openharmony-sig/vendor_winnermicro/pulls) | 1 |5 |1 | 
| [kikainput](https://gitee.com/openharmony-sig/kikainput.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[KIKA](https://gitee.com/kikatech),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/kikainput/issues) | [2](https://gitee.com/openharmony-sig/kikainput/pulls) | 0 |0 |2 | 
| [communication_nfc](https://gitee.com/openharmony-sig/communication_nfc.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/communication_nfc/issues) | [2](https://gitee.com/openharmony-sig/communication_nfc/pulls) | 0 |0 |2 | 
| [miscservices_inputmethod](https://gitee.com/openharmony-sig/miscservices_inputmethod.git) | [mamingshuai](https://gitee.com/landwind),[demon](https://gitee.com/zhouyongfei),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) | input method framework <br /> 输入法框架，可以拉通应用和输入法，保证应用可以通过输入法进行文本输入 | [0](https://gitee.com/openharmony-sig/miscservices_inputmethod/issues) | [14](https://gitee.com/openharmony-sig/miscservices_inputmethod/pulls) | 0 |3 |11 | 
| [online_event](https://gitee.com/openharmony-sig/online_event.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[Kid_li](https://gitee.com/kid-li),[tangr](https://gitee.com/rtan60),[jony](https://gitee.com/jony_code) | 此仓库为demo收集仓库，包含HarmonyOS技术训练营、HarmonyOS线上Codelabs系列挑战赛、HarmonyOS技术征文大赛等线上活动的技术作品。 | [0](https://gitee.com/openharmony-sig/online_event/issues) | [14](https://gitee.com/openharmony-sig/online_event/pulls) | 6 |5 |3 | 
| [device_unionpi](https://gitee.com/openharmony-sig/device_unionpi.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[jiandao.chen](https://gitee.com/chen-jiandao) |  | [0](https://gitee.com/openharmony-sig/device_unionpi/issues) | [6](https://gitee.com/openharmony-sig/device_unionpi/pulls) | 0 |3 |3 | 
| [devboard_device_allwinner_xr806](https://gitee.com/openharmony-sig/devboard_device_allwinner_xr806.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[uncleli](https://gitee.com/moldy-potato-chips),[bruce.cai](https://gitee.com/bruce-caijun),[jony](https://gitee.com/jony_code) |  | [4](https://gitee.com/openharmony-sig/devboard_device_allwinner_xr806/issues) | [15](https://gitee.com/openharmony-sig/devboard_device_allwinner_xr806/pulls) | 0 |3 |12 | 
| [devboard_vendor_allwinner_xr806](https://gitee.com/openharmony-sig/devboard_vendor_allwinner_xr806.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[uncleli](https://gitee.com/moldy-potato-chips),[bruce.cai](https://gitee.com/bruce-caijun),[jony](https://gitee.com/jony_code) |  | [2](https://gitee.com/openharmony-sig/devboard_vendor_allwinner_xr806/issues) | [5](https://gitee.com/openharmony-sig/devboard_vendor_allwinner_xr806/pulls) | 0 |1 |4 | 
| [devboard_device_allwinner_t507](https://gitee.com/openharmony-sig/devboard_device_allwinner_t507.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[bruce.cai](https://gitee.com/bruce-caijun),[JetCui](https://gitee.com/jetcui),[jony](https://gitee.com/jony_code) |  | [3](https://gitee.com/openharmony-sig/devboard_device_allwinner_t507/issues) | [27](https://gitee.com/openharmony-sig/devboard_device_allwinner_t507/pulls) | 0 |5 |22 | 
| [devboard_vendor_allwinner_t507](https://gitee.com/openharmony-sig/devboard_vendor_allwinner_t507.git) | [Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[bruce.cai](https://gitee.com/bruce-caijun),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/devboard_vendor_allwinner_t507/issues) | [1](https://gitee.com/openharmony-sig/devboard_vendor_allwinner_t507/pulls) | 0 |0 |1 | 
| [devboard_applications_sample_talkweb_niobe](https://gitee.com/openharmony-sig/devboard_applications_sample_talkweb_niobe.git) | [Robert](https://gitee.com/minglonghuang),[候鹏飞](https://gitee.com/pengfeihou),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/devboard_applications_sample_talkweb_niobe/issues) | [5](https://gitee.com/openharmony-sig/devboard_applications_sample_talkweb_niobe/pulls) | 0 |4 |1 | 
| [devboard_device_talkweb_niobe](https://gitee.com/openharmony-sig/devboard_device_talkweb_niobe.git) | [Robert](https://gitee.com/minglonghuang),[候鹏飞](https://gitee.com/pengfeihou),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/devboard_device_talkweb_niobe/issues) | [3](https://gitee.com/openharmony-sig/devboard_device_talkweb_niobe/pulls) | 0 |2 |1 | 
| [devboard_vendor_talkweb](https://gitee.com/openharmony-sig/devboard_vendor_talkweb.git) | [Robert](https://gitee.com/minglonghuang),[候鹏飞](https://gitee.com/pengfeihou),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/devboard_vendor_talkweb/issues) | [2](https://gitee.com/openharmony-sig/devboard_vendor_talkweb/pulls) | 0 |0 |2 | 
| [third_party_tinyalsa](https://gitee.com/openharmony-sig/third_party_tinyalsa.git) | [Robert](https://gitee.com/minglonghuang),[XuNan](https://gitee.com/xunan2020),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[xzmu](https://gitee.com/xzmu),[zhao_haipeng](https://gitee.com/zhao_haipeng) | Third-party open-source software tinyalsa <br /> 三方开源软件tinyalsa | [4](https://gitee.com/openharmony-sig/third_party_tinyalsa/issues) | [5](https://gitee.com/openharmony-sig/third_party_tinyalsa/pulls) | 0 |1 |4 | 
| [devboard_vendor_rpi3b](https://gitee.com/openharmony-sig/devboard_vendor_rpi3b.git) | [Robert](https://gitee.com/minglonghuang),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[xfan1024](https://gitee.com/xfan1024),[qwer](https://gitee.com/kevenNO1) |  | [3](https://gitee.com/openharmony-sig/devboard_vendor_rpi3b/issues) | [2](https://gitee.com/openharmony-sig/devboard_vendor_rpi3b/pulls) | 0 |1 |1 | 
| [vendor_unionpi](https://gitee.com/openharmony-sig/vendor_unionpi.git) | [Robert](https://gitee.com/minglonghuang),[jiandao.chen](https://gitee.com/chen-jiandao),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/vendor_unionpi/issues) | [0](https://gitee.com/openharmony-sig/vendor_unionpi/pulls) | 0 |0 |0 | 
| [riscv_device_sunxi](https://gitee.com/openharmony-sig/riscv_device_sunxi.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/riscv_device_sunxi/issues) | [3](https://gitee.com/openharmony-sig/riscv_device_sunxi/pulls) | 0 |1 |2 | 
| [devboard_device_itcast_genkipi](https://gitee.com/openharmony-sig/devboard_device_itcast_genkipi.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/devboard_device_itcast_genkipi/issues) | [5](https://gitee.com/openharmony-sig/devboard_device_itcast_genkipi/pulls) | 0 |4 |1 | 
| [devboard_vendor_itcast_genkipi](https://gitee.com/openharmony-sig/devboard_vendor_itcast_genkipi.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) |  | [0](https://gitee.com/openharmony-sig/devboard_vendor_itcast_genkipi/issues) | [2](https://gitee.com/openharmony-sig/devboard_vendor_itcast_genkipi/pulls) | 0 |1 |1 | 
| [devboard_waffle_nano](https://gitee.com/openharmony-sig/devboard_waffle_nano.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[黑胡桃实验室](https://gitee.com/bw-labs) |  | [0](https://gitee.com/openharmony-sig/devboard_waffle_nano/issues) | [5](https://gitee.com/openharmony-sig/devboard_waffle_nano/pulls) | 0 |3 |2 | 
| [ai_framework_integration](https://gitee.com/openharmony-sig/ai_framework_integration.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) |  | [0](https://gitee.com/openharmony-sig/ai_framework_integration/issues) | [2](https://gitee.com/openharmony-sig/ai_framework_integration/pulls) | 0 |1 |1 | 
| [knowledge_demo_smart_home](https://gitee.com/openharmony-sig/knowledge_demo_smart_home.git) | [Robert](https://gitee.com/minglonghuang),[mamingshuai](https://gitee.com/landwind),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[kenio_zhang](https://gitee.com/kenio_zhang) |  | [5](https://gitee.com/openharmony-sig/knowledge_demo_smart_home/issues) | [95](https://gitee.com/openharmony-sig/knowledge_demo_smart_home/pulls) | 0 |31 |64 | 
| [knowledge](https://gitee.com/openharmony-sig/knowledge.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/knowledge/issues) | [9](https://gitee.com/openharmony-sig/knowledge/pulls) | 0 |1 |8 | 
| [devboard_device_goodix_gr551x](https://gitee.com/openharmony-sig/devboard_device_goodix_gr551x.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[汇顶科技](https://gitee.com/sink-top) |  | [1](https://gitee.com/openharmony-sig/devboard_device_goodix_gr551x/issues) | [16](https://gitee.com/openharmony-sig/devboard_device_goodix_gr551x/pulls) | 0 |4 |12 | 
| [devboard_vendor_goodix_gr5515_sk_basic](https://gitee.com/openharmony-sig/devboard_vendor_goodix_gr5515_sk_basic.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[汇顶科技](https://gitee.com/sink-top) |  | [1](https://gitee.com/openharmony-sig/devboard_vendor_goodix_gr5515_sk_basic/issues) | [7](https://gitee.com/openharmony-sig/devboard_vendor_goodix_gr5515_sk_basic/pulls) | 0 |2 |5 | 
| [accessibility](https://gitee.com/openharmony-sig/accessibility.git) | [mamingshuai](https://gitee.com/landwind),[ydmgr](https://gitee.com/ydmgr),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/accessibility/issues) | [0](https://gitee.com/openharmony-sig/accessibility/pulls) | 0 |0 |0 | 
| [third_party_fsck_msdos](https://gitee.com/openharmony-sig/third_party_fsck_msdos.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/third_party_fsck_msdos/issues) | [0](https://gitee.com/openharmony-sig/third_party_fsck_msdos/pulls) | 0 |0 |0 | 
| [storage_user_file_manger](https://gitee.com/openharmony-sig/storage_user_file_manger.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/storage_user_file_manger/issues) | [1](https://gitee.com/openharmony-sig/storage_user_file_manger/pulls) | 1 |0 |0 | 
| [storage_app_file_manager](https://gitee.com/openharmony-sig/storage_app_file_manager.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/storage_app_file_manager/issues) | [0](https://gitee.com/openharmony-sig/storage_app_file_manager/pulls) | 0 |0 |0 | 
| [storage_app_fileshare_manager](https://gitee.com/openharmony-sig/storage_app_fileshare_manager.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/storage_app_fileshare_manager/issues) | [0](https://gitee.com/openharmony-sig/storage_app_fileshare_manager/pulls) | 0 |0 |0 | 
| [storage_storage_manager](https://gitee.com/openharmony-sig/storage_storage_manager.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/storage_storage_manager/issues) | [0](https://gitee.com/openharmony-sig/storage_storage_manager/pulls) | 0 |0 |0 | 
| [storage_distributed_file_manager](https://gitee.com/openharmony-sig/storage_distributed_file_manager.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/storage_distributed_file_manager/issues) | [2](https://gitee.com/openharmony-sig/storage_distributed_file_manager/pulls) | 0 |1 |1 | 
| [storage_fs_tools](https://gitee.com/openharmony-sig/storage_fs_tools.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/storage_fs_tools/issues) | [0](https://gitee.com/openharmony-sig/storage_fs_tools/pulls) | 0 |0 |0 | 
| [third_party_f2fs-tools](https://gitee.com/openharmony-sig/third_party_f2fs-tools.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/third_party_f2fs-tools/issues) | [0](https://gitee.com/openharmony-sig/third_party_f2fs-tools/pulls) | 0 |0 |0 | 
| [third_party_ntfs-3g](https://gitee.com/openharmony-sig/third_party_ntfs-3g.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/third_party_ntfs-3g/issues) | [0](https://gitee.com/openharmony-sig/third_party_ntfs-3g/pulls) | 0 |0 |0 | 
| [third_party_gptfdisk](https://gitee.com/openharmony-sig/third_party_gptfdisk.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/third_party_gptfdisk/issues) | [0](https://gitee.com/openharmony-sig/third_party_gptfdisk/pulls) | 0 |0 |0 | 
| [third_party_newfs_msdos](https://gitee.com/openharmony-sig/third_party_newfs_msdos.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_ci](https://gitee.com/openharmony_ci),[zhangzhiwi](https://gitee.com/zhangzhiwi),[易见](https://gitee.com/easy-to-see),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/third_party_newfs_msdos/issues) | [0](https://gitee.com/openharmony-sig/third_party_newfs_msdos/pulls) | 0 |0 |0 | 
| [knowledge_demo_temp](https://gitee.com/openharmony-sig/knowledge_demo_temp.git) | [mamingshuai](https://gitee.com/landwind),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[Robert](https://gitee.com/minglonghuang),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/knowledge_demo_temp/issues) | [7](https://gitee.com/openharmony-sig/knowledge_demo_temp/pulls) | 0 |1 |6 | 
| [website_v2](https://gitee.com/openharmony-sig/website_v2.git) | [Robert](https://gitee.com/minglonghuang),[xzmu](https://gitee.com/xzmu),[ChangweiXu](https://gitee.com/changweixu),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[lz](https://gitee.com/bit32) |  | [2](https://gitee.com/openharmony-sig/website_v2/issues) | [13](https://gitee.com/openharmony-sig/website_v2/pulls) | 0 |0 |13 | 
| [device_soc_hisilicon](https://gitee.com/openharmony-sig/device_soc_hisilicon.git) | [mamingshuai](https://gitee.com/landwind),[chenxin](https://gitee.com/northking-super),[hisi_zk](https://gitee.com/hisi_zk),[Aaron_Lv](https://gitee.com/Aaron_Lv),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_soc_hisilicon/issues) | [18](https://gitee.com/openharmony-sig/device_soc_hisilicon/pulls) | 0 |0 |18 | 
| [device_board_hisilicon](https://gitee.com/openharmony-sig/device_board_hisilicon.git) | [mamingshuai](https://gitee.com/landwind),[chenxin](https://gitee.com/northking-super),[hisi_zk](https://gitee.com/hisi_zk),[Aaron_Lv](https://gitee.com/Aaron_Lv),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/device_board_hisilicon/issues) | [10](https://gitee.com/openharmony-sig/device_board_hisilicon/pulls) | 0 |0 |10 | 
| [device_board_fnlink](https://gitee.com/openharmony-sig/device_board_fnlink.git) | [mamingshuai](https://gitee.com/landwind),[SimonLi](https://gitee.com/kkup180),[openharmony_ci](https://gitee.com/openharmony_ci),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [1](https://gitee.com/openharmony-sig/device_board_fnlink/issues) | [13](https://gitee.com/openharmony-sig/device_board_fnlink/pulls) | 0 |3 |10 | 
| [devboard_device_nrf52840dk](https://gitee.com/openharmony-sig/devboard_device_nrf52840dk.git) | [Robert](https://gitee.com/minglonghuang),[Nagesh](https://gitee.com/NageshShamnur),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci) |  | [0](https://gitee.com/openharmony-sig/devboard_device_nrf52840dk/issues) | [0](https://gitee.com/openharmony-sig/devboard_device_nrf52840dk/pulls) | 0 |0 |0 | 
| [third_party_benchmark](https://gitee.com/openharmony-sig/third_party_benchmark.git) | [mamingshuai](https://gitee.com/landwind),[gaohanyi1982](https://gitee.com/gaohanyi1982),[wangjuntao](https://gitee.com/buranfanchen),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/third_party_benchmark/issues) | [5](https://gitee.com/openharmony-sig/third_party_benchmark/pulls) | 0 |4 |1 | 
| [third_party_minimp3](https://gitee.com/openharmony-sig/third_party_minimp3.git) | [Robert](https://gitee.com/minglonghuang),[lijianpeng](https://gitee.com/lijianpeng93),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/third_party_minimp3/issues) | [0](https://gitee.com/openharmony-sig/third_party_minimp3/pulls) | 0 |0 |0 | 
| [third_party_minimp4](https://gitee.com/openharmony-sig/third_party_minimp4.git) | [Robert](https://gitee.com/minglonghuang),[lijianpeng](https://gitee.com/lijianpeng93),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[qwer](https://gitee.com/kevenNO1),[jony](https://gitee.com/jony_code) |  | [0](https://gitee.com/openharmony-sig/third_party_minimp4/issues) | [0](https://gitee.com/openharmony-sig/third_party_minimp4/pulls) | 0 |0 |0 | 
| [device_board_goodix](https://gitee.com/openharmony-sig/device_board_goodix.git) | [Robert](https://gitee.com/minglonghuang),[openharmony_sig_ci](https://gitee.com/openharmony_sig_ci),[jony](https://gitee.com/jony_code),[qwer](https://gitee.com/kevenNO1) |  | [0](https://gitee.com/openharmony-sig/device_board_goodix/issues) | [0](https://gitee.com/openharmony-sig/device_board_goodix/pulls) | 0 |0 |0 | 




# MindIE-Turbo

## 介绍
MindIE Turbo是华为为昇腾芯片开发的大语言模型推理引擎加速插件库，包含自研的大语言模型优化算法及推理引擎相关优化。MindIE Turbo提供一系列模块化和插件化接口，支持外部推理引擎的接入和加速。

目前，MindIE Turbo已支持vLLM的适配。通过与vLLM和vLLM-ascend的对接，能够提供更强的性能和更多的推理优化量化算法。在实际使用中，用户只需在对应的Python环境中安装MindIE Turbo，系统会自动检测vLLM并启用优化，无需修改代码即可完成性能提升。

## 支持框架：
**vLLM**：vLLM是伯克利大学LMSYS组织开源的大语言模型高速推理框架，旨在极大地提升实时场景下的语言模型服务的吞吐率与内存使用率，提供易用、快速、便宜的LLM服务。目前MindIE Turbo已经支持通过vLLM-Ascend一键叠加到vLLM框架并进行推理加速使能。

## 架构说明
MindIE-Turbo主要包含以下模块（部分为预留模块）:

- adaptor: 适配不同推理框架的优化实现
  - vllm: VLLM框架适配
- distributed: 分布式能力支持
- scheduler: 加速调度策略支持
- functional: 通用功能函数
- interface: 通用接口定义
- layers: 网络层实现
- moe: MoE相关实现
- quantize: 量化相关实现
- spec_decode: Speculative Decoding实现
- utils: 通用工具

## 环境准备
### 硬件环境及操作系统准备
- 目前MindIE Turbo支持的硬件环境：Atlas 800I A2 推理产品（32GB/64GB）
- 支持的操作系统请参见《MindIE安装指南》中“环境准备 > 支持的操作系统”章节

### 开发环境准备
在安装MindIE Turbo之前请检查以下组件的配套关系和安装情况：

<!-- 表格标题：组件配套驱动与固件（HDK） -->

| 组件         | 配套版本            | 获取链接       |
| ------------ | ------------------- | -------------- |
| **驱动与固件（HDK）** | >=24.0             | [获取链接](https://support.huawei.com/enterprise/zh/ascend-computing/ascend-hdk-pid-252764743/software)       |
| **CANN**     | >=8.0.0             | [获取链接](https://www.hiascend.com/developer/download/community/result?module=ie%2Bpt%2Bcann)      |
| **PyTorch**  | 2.5.1               | [获取链接](https://www.hiascend.com/developer/download/community/result?module=ie%2Bpt%2Bcann)       |
| **Python**   | 3.10.x、3.11.x      | -              |

1、安装配套版本的驱动与固件（HDK）、CANN软件（Toolkit、Kernels 和 NNAL）请参考《CANN 软件安装指南》，在“选择安装场景”页面，按下列指引选择：
- **安装方式**: 在物理机上安装
- **操作系统**: 根据实际情况选择
- **业务场景**: 选择训练 & 推理 & 开发调试

2、安装PyTorch，请参考组件[安装Pytorch框架](https://www.hiascend.com/document/detail/zh/Pytorch/600/configandinstg/instg/insg_0005.html)与[安装torch_npu插件](https://www.hiascend.com/document/detail/zh/Pytorch/600/configandinstg/instg/insg_0006.html)安装

## 使用说明
### 1. 安装指南
1. 联系相关人员获取 MindIE Turbo 软件包。

2. 将 MindIE Turbo 软件包上传到安装环境的任意路径（例如：`/home/package`）。

3. 进入软件包所在路径：

   ```bash
   cd /home/package
   ```
4. 执行以下命令安装 MindIE Turbo：
   ```bash
   python setup.py install
   ```
5. 返回上级目录，执行以下命令验证是否安装成功：
   ```bash
   cd ../
   pip show mindie_turbo
   ```
   如果出现如下示例结果，表示安装成功：
   ```bash
   Version: 1.0rc1
   Summary: MindIE Turbo: An LLM inference acceleration framework featuring extensive plugin collections optimized for Ascend devices.
   Home-page: 
   Author: ascend
   Author-email: 
   License: Apache 2.0
   Location: /usr/local/lib/python3.11/site-packages
   Requires: filelock, fsspec, jinja2, markupsafe, mpmath, networkx, sympy, torch, typing-extensions
   Required-by: 
   ```

### 2. 快速使用
MindIE Turbo不会修改任何使用行为，与原有框架保持一致，使得用户可以很轻松的应用并迁移项目。以vLLM框架为例：
1. 安装vLLM与vLLM-Ascend。

   请参考[vLLM-Ascend安装文档](https://vllm-ascend.readthedocs.io/en/latest/installation.html)进行安装。

2. 根据需要，进行离线批量推理或在线服务推理。
- 离线批量推理
   请参考[vLLM离线推理示例文档](https://docs.vllm.ai/en/latest/getting_started/quickstart.html#offline-batched-inference)进行推理。以下为最简单的示例（来自[vllm/examples/offline_inference/basic/basic.py](https://github.com/vllm-project/vllm/blob/main/examples/offline_inference/basic/basic.py)，请根据需要修改：
   ```python 
   from vllm import LLM, SamplingParams

   # Sample prompts.
   prompts = [
      "Hello, my name is",
      "The president of the United States is",
      "The capital of France is",
      "The future of AI is",
   ]
   # Create a sampling params object.
   sampling_params = SamplingParams(temperature=0.8, top_p=0.95)

   # Create an LLM.
   llm = LLM(model="facebook/opt-125m")
   # Generate texts from the prompts. The output is a list of RequestOutput objects
   # that contain the prompt, generated text, and other information.
   outputs = llm.generate(prompts, sampling_params)
   # Print the outputs.
   for output in outputs:
      prompt = output.prompt
      generated_text = output.outputs[0].text
      print(f"Prompt: {prompt!r}, Generated text: {generated_text!r}")
   ```
- 启动在线推理服务
请根据[vLLM在线服务示例文档](https://docs.vllm.ai/en/latest/serving/openai_compatible_server.html)启动服务。以下以Qwen2.5-1.5B-Instruct简单示例，请根据需要修改：
   ```bash
   vllm serve Qwen/Qwen2.5-1.5B-Instruct
   ```


### 3. MindIE Turbo环境变量说明
| 环境变量名                           | 默认值 | 功能说明                                      | 配置说明                                      |
|------------------------------------|--------|-------------------------------------------|-------------------------------------------|
| USING_PP_MATMUL                    | 0      | 是否为浮点计算应用ping-pang matmul。 | 0：不应用pp_matmul。 1：应用pp_matmul。                    |
| USING_CPU_TOPP_TOPK                | 0      | 是否应用CPU版本的topp_topk算法进行后处理采样 | 0：关闭应用。 1：开启应用。                    |
| USING_SAMPLING_TENSOR_CACHE        | 0      | 是否启用张量缓存，chunkprefill和beamsearch场景下暂不支持 | 0：不启用。 1：启用。                    |
| USING_LCCL_COM                     | 1      | 是否启用LCCL通信，LCCL通信暂未支持多机通信 | 0：不启用。 1：启用。                    |


## 支持特性
### W8A8量化插件
目前在MindIE Turbo中已经支持了MindStudio自研的W8A8与W8A8QuantAttention算法。通过MindStudio量化的模型可以直接通过MindIE Turbo在vLLM上一键使能。

vLLM及vLLM-Ascend已实现负责量化配置解析的`QuantConfig`、负责对量化方法进行识别和选择的`Quantizer`，MindIE-Turbo将在上述基础上实现`QuantMethod`，即`AscendW8A8LinearMethod`，基于MindIE全栈提供量化实现。

具体而言，`AscendW8A8LinearMethod`提供一下四个接口：
#### get_weight接口
1. 接口功能：

   返回W8A8量化所需要的weight参数名与tensor。

2. 参数说明：


   | 参数名称     | 是否必选 | 类型 | 默认值 | 描述                                      | 安全声明                               |
   | ------------ | -------- | ---- | ------ | ----------------------------------------- | -------------------------------------- |
   | input_size   | 是       | int  | -      | W8A8 linear的输入维度大小。              | 推理强依赖数据的合法性，需由用户保证。 |
   | output_size  | 是       | int  | -      | W8A8 linear的输出维度大小。              | 推理强依赖数据的合法性，需由用户保证。 |

3. 返回值说明

   | 类型                      | 描述                                                    | 安全声明                               |
   | ------------------------- | ------------------------------------------------------- | -------------------------------------- |
   | Dict[str, torch.Tensor]    | 代表W8A8所需的weight参数名与符合形状要求的tensor。      | 推理强依赖数据的合法性，需由用户保证。 |

#### get_pertensor_param接口
1. 接口功能：

   返回W8A8量化所需要的per_tensor参数名与tensor。

2. 参数说明：
   | 参数名称      | 是否必选 | 类型           | 默认值 | 描述                                             | 安全声明                          |
   | ------------- | -------- | -------------- | ------ | ------------------------------------------------ | --------------------------------- |
   | params_dtype  | 是       | torch.dtype    | -      | W8A8 linear的输入参数类型。                      | 推理强依赖数据的合法性，需由用户保证。 |


3. 返回值说明：

   | 返回值名称       | 类型                   | 描述                                                    | 安全声明                          |
   | ---------------- | ---------------------- | ------------------------------------------------------- | --------------------------------- |
   | Dict[str, torch.Tensor] | dict[str, torch.Tensor] | 代表W8A8所需的pertensor参数名与符合形状要求的tensor。  | 推理强依赖数据的合法性，需由用户保证。 |


#### get_perchannel_param接口

1. 接口功能：

   返回W8A8量化所需要的per_channel参数名与tensor。

2. 参数说明：

   | 参数名称      | 是否必选 | 类型           | 默认值 | 描述                                             | 安全声明                          |
   | ------------- | -------- | -------------- | ------ | ------------------------------------------------ | --------------------------------- |
   | output_size   | 是       | int            | -      | W8A8 linear的输出维度大小。                      | 推理强依赖数据的合法性，需由用户保证。 |
   | params_dtype  | 是       | torch.dtype    | -      | W8A8 linear的输出参数类型。                      | 推理强依赖数据的合法性，需由用户保证。 |

3. 返回值说明：


   | 返回值名称       | 类型                   | 描述                                                    | 安全声明                          |
   | ---------------- | ---------------------- | ------------------------------------------------------- | --------------------------------- |
   | Dict[str, torch.Tensor] | dict[str, torch.Tensor] | 代表W8A8所需的perchannel参数名与符合形状要求的tensor。  | 推理强依赖数据的合法性，需由用户保证。 |

#### apply接口
1. 接口功能：

   实现W8A8 linear所需的前向计算。

2. 参数说明：

   | 参数名称      | 是否必选 | 类型             | 默认值 | 描述                                                                         | 安全声明                          |
   | ------------- | -------- | ---------------- | ------ | ---------------------------------------------------------------------------- | --------------------------------- |
   | layer         | 是       | torch.nn.Module   | -      | 被量化后的一个linear对象，并且必须注册了由get_weiget、get_perchannel_param、get_pertensor_param所给出的参数。 | 推理强依赖数据的合法性，需由用户保证。 |
   | x             | 是       | torch.Tensor      | -      | 量化linear前向计算的输入。                                                   | 推理强依赖数据的合法性，需由用户保证。 |

3. 返回值说明：

    | 类型           | 描述                                           | 安全声明                          |
    | -------------- | ---------------------------------------------- | --------------------------------- |
    | torch.Tensor   | 量化linear的前向计算结果                      | 推理强依赖数据的合法性，需由用户保证。 |

## 参与贡献

1. Fork 本仓库
2. 新建分支
3. 验证修改
4. 提交代码
5. 新建 Pull Request
