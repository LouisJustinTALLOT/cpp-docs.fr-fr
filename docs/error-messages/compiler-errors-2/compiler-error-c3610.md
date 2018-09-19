---
title: Erreur du compilateur C3610 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46b3669978ff3735d5a16015ca0a01e65f07ae9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037851"
---
# <a name="compiler-error-c3610"></a>Erreur du compilateur C3610

'valuetype' : type de valeur doit être 'boxed' avant l’appel de méthode 'method'

Par défaut, un type valeur n’est pas sur le tas managé. Avant que vous pouvez appeler des méthodes à partir de classes de runtime .NET, tel que `Object`, vous devez déplacer le type de valeur dans le tas managé.

C3610 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**.
