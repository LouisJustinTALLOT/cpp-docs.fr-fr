---
title: Erreur du compilateur C3859 | Documents Microsoft
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
ms.openlocfilehash: d2f8c51f25c09881e10e980276fc2035a6a70aed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272303"
---
# <a name="compiler-error-c3859"></a>Erreur du compilateur C3859
plage de mémoire virtuelle dépassée pour PCH ; recompilez avec une option de ligne de commande ’-Zmvalue’ ou supérieur  
  
 Votre en-tête précompilé est trop petit pour la quantité de données que le compilateur tente d’y placer. Utilisez le **/Zm** indicateur de compilateur pour spécifier une valeur supérieure pour le fichier d’en-tête précompilé. Pour plus d’informations, consultez [/Zm (spécifier précompilés en-tête limite d’Allocation mémoire)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).