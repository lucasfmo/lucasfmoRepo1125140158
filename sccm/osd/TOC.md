# Megértés és felfedezés
## [Bevezetés az operációs rendszerek központi telepítésébe](understand/introduction-to-operating-system-deployment.md)
## [A feladatütemezés lépései](understand/task-sequence-steps.md)
## [A feladatütemezés műveleti változói](understand/task-sequence-action-variables.md)
## [A feladatütemezés beépített változói](understand/task-sequence-built-in-variables.md)
## [A feladatütemezési adathordozók indítás előtti parancsai](understand/prestart-commands-for-task-sequence-media.md)

# Tervezés és kialakítás
## [Az operációs rendszerek központi telepítésének infrastrukturális követelményei](plan-design/infrastructure-requirements-for-operating-system-deployment.md)
## [Tervezési megfontolások a feladatok automatizálásához](plan-design/planning-considerations-for-automating-tasks.md)
## [Biztonsági és adatvédelmi tudnivalók az operációs rendszerek központi telepítésével kapcsolatban](plan-design/security-and-privacy-for-operating-system-deployment.md)
## [Együttműködés tervezése operációs rendszerek központi telepítései között](plan-design/planning-for-operating-system-deployment-interoperability.md)

# Első lépések
## [Helyrendszerszerepkörök előkészítése operációs rendszerek központi telepítéséhez](get-started/prepare-site-system-roles-for-operating-system-deployments.md)
## [Operációs rendszerek központi telepítésének előkészítése](get-started/prepare-for-operating-system-deployment.md)
### [Rendszerindító lemezképek kezelése](get-started/manage-boot-images.md)
#### [Rendszerindító lemezképek testreszabása](get-started/customize-boot-images.md)

### [Operációsrendszer-lemezképek kezelése](get-started/manage-operating-system-images.md)
#### [Operációsrendszer-lemezképek testreszabása](get-started/customize-operating-system-images.md)

### [Operációs rendszerek verziófrissítő csomagjainak kezelése](get-started/manage-operating-system-upgrade-packages.md)
### [Illesztőprogramok kezelése](get-started/manage-drivers.md)
### [Felhasználói állapot kezelése](get-started/manage-user-state.md)
### [Felkészülés ismeretlen számítógépek központi telepítésére](get-started/prepare-for-unknown-computer-deployments.md)
### [Felhasználók társítása célszámítógéphez](get-started/associate-users-with-a-destination-computer.md)

## [Windows PE-társgyorsítótár előkészítése a WAN-hálózati forgalom csökkentése érdekében](get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md)

# Központi telepítés és használat
## [A vállalati operációs rendszerek központi telepítésének forgatókönyvei](deploy-use/scenarios-to-deploy-enterprise-operating-systems.md)
### [A Windows frissítése a legújabb verzióra](deploy-use/upgrade-windows-to-the-latest-version.md)
### [Meglévő számítógép frissítése a Windows új verziójára](deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md)
### [A Windows új verziójának telepítése új (operációs rendszer nélküli) gépen](deploy-use/install-new-windows-version-new-computer-bare-metal.md)
### [Meglévő számítógép cseréje és a beállítások átvitele](deploy-use/replace-an-existing-computer-and-transfer-settings.md)

## [A vállalati operációs rendszerek központi telepítésének módszerei](deploy-use/methods-to-deploy-enterprise-operating-systems.md)
### [A Windows központi telepítése a hálózaton keresztül PXE használatával](deploy-use/use-pxe-to-deploy-windows-over-the-network.md)
### [A Windows központi telepítése a hálózaton keresztül a Szoftverközpont használatával](deploy-use/use-software-center-to-deploy-windows-over-the-network.md)
### [A Windows központi telepítése a hálózaton keresztül rendszerindító adathordozó használatával](deploy-use/use-bootable-media-to-deploy-windows-over-the-network.md)
### [A Windows központi telepítése különálló adathordozóval, a hálózat használata nélkül](deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network.md)
### [A Windows központi telepítése a hálózaton keresztül csoportos küldéssel](deploy-use/use-multicast-to-deploy-windows-over-the-network.md)
### [Lemezkép létrehozása OEM-gyár vagy helyi raktár számára](deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md)
### [A Windows to Go központi telepítése](deploy-use/deploy-windows-to-go.md)

## [A Windows rendszer kezelése szolgáltatásként](deploy-use/manage-windows-as-a-service.md)
## [Operációs rendszerek központi telepítésének figyelése](deploy-use/monitor-operating-system-deployments.md)

## [Feladatütemezések kezelése feladatok automatizálásához](deploy-use/manage-task-sequences-to-automate-tasks.md)
### [Feladatütemezés létrehozása operációs rendszer telepítéséhez](deploy-use/create-a-task-sequence-to-install-an-operating-system.md)
### [Feladatütemezés létrehozása operációs rendszer verziófrissítéséhez](deploy-use/create-a-task-sequence-to-upgrade-an-operating-system.md)
### [Feladatütemezés létrehozása operációs rendszer rögzítéséhez](deploy-use/create-a-task-sequence-to-capture-an-operating-system.md)
### [Feladatütemezés létrehozása felhasználói állapotadatok rögzítéséhez és helyreállításához](deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md)
### [Virtuális merevlemezek kezelése feladatütemezés használatával](deploy-use/use-a-task-sequence-to-manage-virtual-hard-disks.md)

## [Egyéni feladatütemezési forgatókönyvek](deploy-use/custom-task-sequence-scenarios.md)
### [Egyéni feladatütemezés létrehozása](deploy-use/create-a-custom-task-sequence.md)
### [Feladatütemezés létrehozása az operációs rendszerektől eltérő telepítésekhez](deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md)
### [Feladatütemezési lépések BIOS-UEFI átalakításhoz](deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion.md)
### [A BitLocker előzetes kiépítése Windows PE-környezetben](deploy-use/preprovision-bitlocker-in-windows-pe.md)

## [Feladatütemezési adathordozó létrehozása](deploy-use/create-task-sequence-media.md)
### [Különálló adathordozó létrehozása](deploy-use/create-stand-alone-media.md)
### [Manuálisan előkészített adathordozó létrehozása](deploy-use/create-prestaged-media.md)
### [Rendszerindító adathordozó létrehozása](deploy-use/create-bootable-media.md)
### [Médiarögzítésű adathordozó létrehozása](deploy-use/create-capture-media.md)
