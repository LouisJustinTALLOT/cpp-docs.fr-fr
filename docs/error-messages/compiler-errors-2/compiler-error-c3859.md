---
title: Erreur du compilateur C3859 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac06a09a6ad66384fd2b5423e3df046771f7653
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053387"
---
# <a name="compiler-error-c3859"></a>Erreur du compilateur C3859

plage de mémoire virtuelle dépassée pour PCH ; recompilez avec une option de ligne de commande ’-Zmvalue’ ou supérieur

Votre en-tête précompilé est trop petit pour la quantité de données que le compilateur tente d’y placer. Utilisez le **/Zm** indicateur de compilateur pour spécifier une valeur supérieure pour le fichier d’en-tête précompilé. Pour plus d’informations, consultez [/Zm (spécifier précompilé en-tête limite d’Allocation mémoire)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).