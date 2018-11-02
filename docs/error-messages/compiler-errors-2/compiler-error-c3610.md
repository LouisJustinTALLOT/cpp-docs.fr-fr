---
title: Erreur du compilateur C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 9965e6420171b2ea48c8fb7bacc0a5a37ea2f227
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591059"
---
# <a name="compiler-error-c3610"></a>Erreur du compilateur C3610

'valuetype' : type de valeur doit être 'boxed' avant l’appel de méthode 'method'

Par défaut, un type valeur n’est pas sur le tas managé. Avant que vous pouvez appeler des méthodes à partir de classes de runtime .NET, tel que `Object`, vous devez déplacer le type de valeur dans le tas managé.

C3610 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**.
