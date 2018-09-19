---
title: Erreur du compilateur C3180 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3180
dev_langs:
- C++
helpviewer_keywords:
- C3180
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e200a75164c0d7fdb0c6804d084630cc6e6007e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048368"
---
# <a name="compiler-error-c3180"></a>Erreur du compilateur C3180

'type name' : nom dépasse la limite métadonnées de 'limite' caractères

Le compilateur a tronqué le nom d’un type managé dans les métadonnées. La troncation rendra le type inutilisable avec la `#using` directive (ou son équivalent dans une autre langue).

La limite de nom de type inclut des qualifications d’espace de noms.