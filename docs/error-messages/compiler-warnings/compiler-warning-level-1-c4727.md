---
title: Avertissement du compilateur (niveau 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 0c00ac552e525fd57f6f09b0be5655958cfce3cc
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075138"
---
# <a name="compiler-warning-level-1-c4727"></a>Avertissement du compilateur (niveau 1) C4727

«PCH nommé pch_file avec le même horodatage trouvé dans obj_file_1 et obj_file_2.  Utilisation du premier PCH.

> [!NOTE]
> Dans Visual Studio 2017 et les versions antérieures, l’en-tête précompilé est appelé *stdafx. h* par défaut, et dans visual studio 2019 et versions ultérieures, il est appelé *pch. h* par défaut.

C4727 se produit lors de la compilation de plusieurs compilands avec **/Yc**, et où le compilateur a pu marquer tous les fichiers. obj avec le même horodatage. pch.

Pour résoudre le, compilez un fichier source avec **/Yc/c** (crée PCH) et les autres compilent séparément avec **/Yu/c** (utilise PCH), puis liez-les ensemble.

Par conséquent, si vous avez effectué les opérations suivantes et qu’il génère C4727 :

::: moniker range="<=vs-2017"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycstdafx.h**

À la place, procédez comme suit :

**CL/CLR/GL a. cpp/Ycstdafx.h/c**

**CL/CLR/GL b. cpp c. cpp/Yustdafx.h/Link a. obj**

::: moniker-end

::: moniker range=">=vs-2019"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycpch.h**

À la place, procédez comme suit :

**CL/CLR/GL a. cpp/Ycpch.h/c**

**CL/CLR/GL b. cpp c. cpp/Yupch.h/Link a. obj**

::: moniker-end

Pour plus d'informations, consultez la rubrique

- [/Yc (Créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (Utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md)