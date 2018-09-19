---
title: jitintrinsic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 888ec19eaedf881fed97a14a7f3f8b5ee673ce7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056285"
---
# <a name="jitintrinsic"></a>jitintrinsic

Marque la fonction comme significative pour le CLR (Common Langage Runtime) 64 bits. Ceci est utilisé pour certaines fonctions dans les bibliothèques fournies par Microsoft.

## <a name="syntax"></a>Syntaxe

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Notes

**jitintrinsic** ajoute un MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) à une signature de fonction.

Les utilisateurs sont déconseillés à partir de l’utilisation de cette **__declspec** modificateur, car des résultats inattendus peut se produire.

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)