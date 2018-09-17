---
title: États du module d’une DLL MFC normale liée de manière dynamique aux MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d458c445930896fb04cb339c7191f649be542faf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717026"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>États du module d’une DLL MFC normale liée de manière dynamique aux MFC

La possibilité de lier de manière dynamique une DLL MFC normale à la DLL MFC permet quelques configurations qui sont très complexes. Par exemple, une DLL MFC normale et l’exécutable qui l’utilise peuvent tous deux lier dynamiquement à la DLL de MFC et à toute DLL d’extension MFC.

Cette configuration pose un problème en ce qui concerne les données globales MFC, telles que le pointeur actuel `CWinApp` objet et gérer des mappages.

Avant la version 4.0 de MFC, ces données globales résidaient dans la DLL MFC elle-même et a été partagées par tous les modules dans le processus. Étant donné que chaque processus à l’aide d’une DLL Win32 obtient sa propre copie des données de la DLL, ce schéma fourni un moyen simple pour effectuer le suivi des données par processus. En outre, comme le modèle AFXDLL qu’il y aurait qu’un seul `CWinApp` objet et qu’un seul jeu de tables de handles dans le processus, ces éléments pouvaient être suivis dans la DLL MFC elle-même.

Mais avec la possibilité de lier de manière dynamique une DLL MFC normale à la DLL MFC, il est désormais possible d’avoir deux ou plusieurs `CWinApp` objets dans un processus — et également deux ou plusieurs jeux de tables de handles. Comment MFC conserver le suivi des celles qui doivent être à l’aide ?

La solution consiste à donner à chaque module (application ou DLL MFC normale) sa propre copie de ces informations d’état global. Par conséquent, un appel à **AfxGetApp** dans la mise à jour les DLL MFC retourne un pointeur vers le `CWinApp` objet dans la DLL, et non celui dans l’exécutable. Cette copie par module des données globales MFC est connue comme un état du module et est décrite dans [MFC Technical Note 58](../mfc/tn058-mfc-module-state-implementation.md).

La procédure de fenêtre MFC courants bascule automatiquement vers l’état du module correct, donc vous n’avez pas besoin de vous inquiéter dans les gestionnaires de messages implémentés dans la DLL MFC normale. Mais quand l’exécutable appelle la DLL MFC normale, vous n’avez pas besoin de définir explicitement l’état du module en cours à celui de la DLL. Pour ce faire, utilisez le **AFX_MANAGE_STATE** macro dans chaque fonction exportée à partir de la DLL. Cette opération est effectuée en ajoutant la ligne de code suivante au début des fonctions exportées à partir de la DLL :

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [DLL MFC normales liées de manière dynamique aux MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC](../build/extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)