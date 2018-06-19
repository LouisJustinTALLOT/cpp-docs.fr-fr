---
title: -SAFESEH (Image a des gestionnaires d’exceptions sécurisés) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54d13e6922650f0193d4bbc3469d4acf25904234
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377907"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (L'image est dotée de gestionnaires d'exceptions sécurisés)
```  
/SAFESEH[:NO]  
```  
  
 Lorsque **/SAFESEH** est spécifié, l’éditeur de liens génère uniquement une image si elle peut également produire une table de gestionnaires d’exceptions sécurisés de l’image. Ce tableau indique le système d’exploitation les gestionnaires d’exceptions sont valides pour l’image.  
  
 **/SAFESEH** est valide uniquement lors de la liaison pour x86 cibles. **/SAFESEH** n’est pas prise en charge pour les plateformes qui ont déjà les gestionnaires d’exceptions. Par exemple, sur [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] et ARM, tous les gestionnaires sont indiqués dans le PDATA d’exception. Ml64.exe est prise en charge pour l’ajout d’annotations qui émettent des informations SEH (XDATA et PDATA) dans l’image, ce qui vous permet de déroulement via les fonctions ml64. Consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) pour plus d’informations.  
  
 Si **/SAFESEH** n’est pas spécifié, l’éditeur de liens génère une image avec une table de gestionnaires d’exceptions sécurisés si tous les modules sont compatibles avec la fonctionnalité de gestion sécurisée des exceptions. Si tous les modules ne sont pas compatibles avec la fonctionnalité de gestion sécurisée des exceptions, l’image résultante ne contiendra pas une table de gestionnaires d’exceptions sécurisés. Si [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) spécifie WINDOWSCE ou l’une des options EFI_ *, l’éditeur de liens ne tente pas de produire une image avec une table de gestionnaires d’exceptions sécurisés, car aucun de ces sous-systèmes peuvent utiliser les informations.  
  
 Si **/SAFESEH : no** est spécifié, l’éditeur de liens ne produira pas une image avec une table de gestionnaires d’exceptions sécurisés même si tous les modules sont compatibles avec la fonctionnalité de gestion sécurisée des exceptions.  
  
 La raison la plus courante de l’éditeur de liens ne pas pouvoir produire une image est, car un ou plusieurs des fichiers d’entrée (modules) à l’éditeur de liens n’étaient pas compatible avec la fonctionnalité de gestionnaires d’exceptions sécurisés. Une raison courante d’un module ne soit ne pas compatible avec les gestionnaires d’exceptions sécurisés est, car il a été créé avec un compilateur d’une version antérieure de Visual C++.  
  
 Vous pouvez également enregistrer une fonction en tant que gestionnaire d’exceptions structuré à l’aide de [. SAFESEH](../../assembler/masm/dot-safeseh.md).  
  
 Il n’est pas possible de marquer un fichier binaire comme ayant des gestionnaires d’exceptions sécurisés (ou aucun gestionnaire d’exceptions) ; plus d’informations sur la gestion des exceptions sécurisés doivent être ajoutées au moment de la génération.  
  
 Capacité de l’éditeur de liens pour générer une table de gestionnaires d’exceptions sécurisés dépend de l’application à l’aide de la bibliothèque runtime C. Si vous liez avec [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) et que vous souhaitez créer une table de gestionnaires d’exceptions sécurisés, vous devez fournir une structure de configuration de charge (par exemple, vous trouverez dans le fichier source CRT loadcfg.c) qui contient toutes les entrées définies pour Visual C++. Par exemple :  
  
```  
#include <windows.h>  
extern DWORD_PTR __security_cookie;  /* /GS security cookie */  
  
/*  
 * The following two names are automatically created by the linker for any  
 * image that has the safe exception table present.  
*/  
  
extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */  
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is  
                                           the count of table entries */  
typedef struct {  
    DWORD       Size;  
    DWORD       TimeDateStamp;  
    WORD        MajorVersion;  
    WORD        MinorVersion;  
    DWORD       GlobalFlagsClear;  
    DWORD       GlobalFlagsSet;  
    DWORD       CriticalSectionDefaultTimeout;  
    DWORD       DeCommitFreeBlockThreshold;  
    DWORD       DeCommitTotalFreeThreshold;  
    DWORD       LockPrefixTable;            // VA  
    DWORD       MaximumAllocationSize;  
    DWORD       VirtualMemoryThreshold;  
    DWORD       ProcessHeapFlags;  
    DWORD       ProcessAffinityMask;  
    WORD        CSDVersion;  
    WORD        Reserved1;  
    DWORD       EditList;                   // VA  
    DWORD_PTR   *SecurityCookie;  
    PVOID       *SEHandlerTable;  
    DWORD       SEHandlerCount;  
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;  
  
const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {  
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    &__security_cookie,  
    __safe_se_handler_table,  
    (DWORD)(DWORD_PTR) &__safe_se_handler_count  
};  
```  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **l’éditeur de liens** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Entrez l’option dans le **des Options supplémentaires** boîte.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)