---
title: Erreur du compilateur C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 9b20224207ba797c6ee93c06404e4d90c3d02525
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738651"
---
# <a name="compiler-error-c3859"></a>Erreur du compilateur C3859

> plage de mémoire virtuelle dépassée pour PCH ; recompilez avec une option de ligne de commande '-Zm*valeur*' ou supérieur

La mémoire virtuelle allouée pour votre en-tête précompilé est trop petite pour la quantité de données, que le compilateur essaie d’insérer dans celui-ci. À compter de Visual Studio 2015, le **/Zm** recommandation est significative uniquement lorsque vous utilisez la `#pragma hdrstop` directive. Dans d’autres cas, il s’agit d’une erreur de fausse qui indique des problèmes de sollicitation de la mémoire virtuelle Windows.

Si votre en-tête précompilé utilise un `#pragma hdrstop` directive, utilisez le **/Zm** indicateur de compilateur pour spécifier une valeur supérieure pour le fichier d’en-tête précompilé. Sinon, envisagez de réduire le nombre de processus de compilation parallèle dans votre build. Pour plus d’informations, consultez [/Zm (spécifier précompilé en-tête limite d’Allocation mémoire)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).
