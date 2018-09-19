---
title: Coprocesseur à virgule flottante et Conventions d’appel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9f45f73e3cb1910bfc604c8a0fde871cef973a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075954"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesseur à virgule flottante et conventions d’appel

Si vous écrivez des routines pour flottante point coprocesseur assembly, vous devez conserver flottante pointez le mot de contrôle et de nettoyer la pile de coprocesseur, sauf si vous retournez un **float** ou **double** valeur (laquelle votre fonction doit retourner dans ST(0)).

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)