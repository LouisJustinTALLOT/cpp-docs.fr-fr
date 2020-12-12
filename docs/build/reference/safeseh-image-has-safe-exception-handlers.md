---
description: En savoir plus sur:/SAFESEH (l’image est dotée de gestionnaires d’exceptions sécurisés)
title: /SAFESEH (L'image est dotée de gestionnaires d'exceptions sécurisés)
ms.date: 11/04/2016
f1_keywords:
- /SAFESEH
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
ms.openlocfilehash: 723b5503bca1d98d7df0c638df1dfc8101fc116f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224983"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (L'image est dotée de gestionnaires d'exceptions sécurisés)

```
/SAFESEH[:NO]
```

Lorsque **/SAFESEH** est spécifié, l’éditeur de liens produira uniquement une image s’il peut également générer une table des gestionnaires d’exceptions sécurisés de l’image. Ce tableau spécifie pour le système d’exploitation les gestionnaires d’exceptions qui sont valides pour l’image.

**/SAFESEH** est uniquement valide lors de la liaison pour les cibles x86. **/SAFESEH** n’est pas pris en charge pour les plateformes qui ont déjà les gestionnaires d’exceptions notés. Par exemple, sur x64 et ARM, tous les gestionnaires d’exceptions sont notés dans le PDATA. ML64.exe prend en charge l’ajout d’annotations qui émettent des informations SEH (XDATA et PDATA) dans l’image, ce qui vous permet de parcourir les fonctions ml64. Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) .

Si **/SAFESEH** n’est pas spécifié, l’éditeur de liens produit une image avec une table de gestionnaires d’exceptions sécurisés si tous les modules sont compatibles avec la fonctionnalité de gestion sécurisée des exceptions. Si des modules n’étaient pas compatibles avec la fonctionnalité de gestion sécurisée des exceptions, l’image résultante ne contient pas de table de gestionnaires d’exceptions sécurisés. Si [/Subsystem](subsystem-specify-subsystem.md) spécifie WindowsCE ou l’une des options EFI_ *, l’éditeur de liens ne tente pas de produire une image avec une table de gestionnaires d’exceptions sécurisés, car aucun de ces sous-systèmes ne peut utiliser les informations.

Si **/SAFESEH : no** est spécifié, l’éditeur de liens ne produira pas d’image avec une table de gestionnaires d’exceptions sécurisés même si tous les modules sont compatibles avec la fonctionnalité de gestion sécurisée des exceptions.

La raison la plus courante pour laquelle l’éditeur de liens n’est pas en mesure de générer une image est qu’un ou plusieurs fichiers d’entrée (modules) de l’éditeur de liens ne sont pas compatibles avec la fonctionnalité des gestionnaires d’exceptions sécurisés. Une raison courante pour laquelle un module n’est pas compatible avec les gestionnaires d’exceptions sécurisés est qu’il a été créé avec un compilateur issu d’une version antérieure de Visual C++.

Vous pouvez également inscrire une fonction en tant que gestionnaire d’exceptions structurées à l’aide de [. SAFESEH](../../assembler/masm/dot-safeseh.md).

Il n’est pas possible de marquer un fichier binaire existant comme ayant des gestionnaires d’exceptions sécurisés (ou aucun gestionnaire d’exceptions); des informations sur la gestion sécurisée des exceptions doivent être ajoutées au moment de la génération.

La capacité de l’éditeur de liens à générer une table de gestionnaires d’exceptions sécurisés dépend de l’application qui utilise la bibliothèque Runtime C. Si vous liez avec [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) et souhaitez une table de gestionnaires d’exceptions sécurisés, vous devez fournir une structure de configuration de charge (par exemple, dans le fichier source CRT loadcfg. c) qui contient toutes les entrées définies pour Visual C++. Par exemple :

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Entrez l’option dans la zone **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
