---
title: Erreur du compilateur C3859
ms.date: 11/04/2016
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: be6ccaab49cb329e862fb6068af1337eddbaac8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490273"
---
# <a name="compiler-error-c3859"></a>Erreur du compilateur C3859

plage de mémoire virtuelle dépassée pour PCH ; recompilez avec une option de ligne de commande ’-Zmvalue’ ou supérieur

Votre en-tête précompilé est trop petit pour la quantité de données que le compilateur tente d’y placer. Utilisez le **/Zm** indicateur de compilateur pour spécifier une valeur supérieure pour le fichier d’en-tête précompilé. Pour plus d’informations, consultez [/Zm (spécifier précompilé en-tête limite d’Allocation mémoire)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).