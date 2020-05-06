---
title: États du module d’une DLL MFC normale liée de manière dynamique aux MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220581"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>États du module d’une DLL MFC normale liée de manière dynamique aux MFC

La possibilité de lier dynamiquement une DLL MFC normale à la DLL MFC autorise certaines configurations très compliquées. Par exemple, une DLL MFC normale et l’exécutable qui l’utilise peuvent être liés de manière dynamique à la DLL MFC et à toutes les dll d’extension MFC.

Cette configuration pose un problème concernant les données globales MFC, telles que le pointeur vers l’objet actuel `CWinApp` et les mappages de handles.

Avant la version 4,0 de MFC, ces données globales se trouvaient dans la DLL MFC elle-même et étaient partagées par tous les modules du processus. Étant donné que chaque processus utilisant une DLL Win32 obtient sa propre copie des données de la DLL, ce schéma offre un moyen simple de suivre les données par processus. En outre, étant donné que le modèle AFXDLL supposait qu’il n' `CWinApp` y avait qu’un seul objet et un seul ensemble de mappages de handle dans le processus, ces éléments pouvaient être suivis dans la DLL MFC elle-même.

Toutefois, avec la possibilité de lier de manière dynamique une DLL MFC normale à la DLL MFC, il est désormais possible d’avoir deux `CWinApp` objets ou plus dans un processus, ainsi qu’au moins deux jeux de mappages de handle. Comment les MFC assurent-elles le suivi des éléments à utiliser ?

La solution consiste à attribuer à chaque module (application ou DLL MFC normale) sa propre copie de ces informations d’État globales. Ainsi, un appel à **AfxGetApp** dans la DLL MFC normale retourne un pointeur vers l' `CWinApp` objet dans la dll, pas celui du fichier exécutable. Cette copie par module des données globales MFC est connue sous le nom d’état de module et est décrite dans [MFC Technical Note 58](../mfc/tn058-mfc-module-state-implementation.md).

La procédure de fenêtre commune MFC bascule automatiquement vers l’état de module approprié. vous n’avez donc pas à vous en soucier dans les gestionnaires de messages implémentés dans votre DLL MFC standard. Toutefois, lorsque votre exécutable appelle la DLL MFC normale, vous devez définir explicitement l’état du module actuel à celui de la DLL. Pour ce faire, utilisez la macro **AFX_MANAGE_STATE** dans chaque fonction exportée à partir de la dll. Pour ce faire, ajoutez la ligne de code suivante au début des fonctions exportées à partir de la DLL :

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Dll d’extension MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
