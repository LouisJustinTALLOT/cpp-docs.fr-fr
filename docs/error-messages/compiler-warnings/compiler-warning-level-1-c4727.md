---
title: Avertissement du compilateur (niveau 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: e1eeb7e466e325772d6a1522e77983fd3de04293
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923962"
---
# <a name="compiler-warning-level-1-c4727"></a>Avertissement du compilateur (niveau 1) C4727

«PCH nommé pch_file avec le même horodatage trouvé dans obj_file_1 et obj_file_2.  Utilisation du premier PCH.

> [!NOTE]
> Dans Visual Studio 2017 et les versions antérieures, l’en-tête précompilé est appelé *stdafx. h* par défaut, et dans visual studio 2019 et versions ultérieures, il est appelé *pch. h* par défaut.

C4727 se produit lors de la compilation de plusieurs compilands avec **/Yc** , et où le compilateur a pu marquer tous les fichiers. obj avec le même horodatage. pch.

Pour résoudre le, compilez un fichier source avec **/Yc/c** (crée PCH) et les autres compilent séparément avec **/Yu/c** (utilise PCH), puis liez-les ensemble.

Par conséquent, si vous avez effectué les opérations suivantes et qu’il génère C4727 :

::: moniker range="<=msvc-150"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycstdafx.h**

À la place, procédez comme suit :

**CL/CLR/GL a. cpp/Ycstdafx.h/c**

**CL/CLR/GL b. cpp c. cpp/Yustdafx.h/Link a. obj**

::: moniker-end

::: moniker range=">=msvc-160"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycpch.h**

À la place, procédez comme suit :

**CL/CLR/GL a. cpp/Ycpch.h/c**

**CL/CLR/GL b. cpp c. cpp/Yupch.h/Link a. obj**

::: moniker-end

Pour plus d'informations, consultez la rubrique

- [/YC (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md)
