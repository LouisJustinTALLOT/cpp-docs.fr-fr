---
title: Erreur irrécupérable C1853 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa6a67c13f76b0bf43159b9e9de95068102a2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229207"
---
# <a name="fatal-error-c1853"></a>Erreur irrécupérable C1853
  
> '*nom de fichier*' fichier d’en-tête précompilé est d’une version antérieure du compilateur, ou l’en-tête précompilé est en C++ et vous l’utilisez en C (ou inversement)  
  
Causes possibles :  
  
-   L’en-tête précompilé a été compilé avec une version précédente de compilateur. Essayez de recompiler l’en-tête avec le compilateur actuel.  
  
-   L’en-tête précompilé est en C++ et vous l’utilisez de réessayez C. recompiler l’en-tête pour une utilisation avec C en spécifiant l’une de le [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) options du compilateur, ou en remplaçant le suffixe du fichier source par « c ». Pour plus d’informations, consultez [deux possibilités pour précompiler le Code](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).