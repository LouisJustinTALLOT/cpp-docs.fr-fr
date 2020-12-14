---
description: 'En savoir plus sur : erreur du compilateur C3610'
title: Erreur du compilateur C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 0fca8f57fcdf2e935620118092708ba1c94f5ec0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223137"
---
# <a name="compiler-error-c3610"></a>Erreur du compilateur C3610

'ValueType' : le type valeur doit être’boxed’avant que la méthode’Method’puisse être appelée

Par défaut, un type valeur ne se trouve pas sur le tas managé. Avant de pouvoir appeler des méthodes à partir de classes Runtime .NET, telles que `Object` , vous devez déplacer le type valeur vers le tas managé.

C3610 est accessible uniquement à l’aide de l’option de compilateur obsolète **/clr : oldSyntax**.
