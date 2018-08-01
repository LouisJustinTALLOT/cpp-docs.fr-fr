---
title: Abort, fonction | Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5679ce718c564ee40fb07b676756ef79344a99
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403620"
---
# <a name="abort-function"></a>abort, fonction

Le **abandonner** fonction, déclarée également dans le fichier include standard \<stdlib.h >, met fin à un programme C++. La différence entre `exit` et **abandonner** qui est `exit` permet le traitement de terminaison d’exécution C++ se déroulent (objet global destructeurs seront appelés), tandis que **abandonner** arrête le programme immédiatement. Pour plus d’informations, consultez [abandonner](../c-runtime-library/reference/abort.md) dans le *Run-Time Library Reference*.

## <a name="see-also"></a>Voir aussi
[Terminaison du programme](../cpp/program-termination.md)