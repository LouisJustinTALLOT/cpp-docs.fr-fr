---
description: 'En savoir plus sur : jitintrinsic'
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: 29f4db3e946d2ccf0ec96bb0248e751bb9297db5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291998"
---
# <a name="jitintrinsic"></a>jitintrinsic

Marque la fonction comme significative pour le CLR (Common Langage Runtime) 64 bits. Ceci est utilisé pour certaines fonctions dans les bibliothèques fournies par Microsoft.

## <a name="syntax"></a>Syntaxe

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Notes

**`jitintrinsic`** Ajoute un MODOPT ( <xref:System.Runtime.CompilerServices.IsJitIntrinsic> ) à une signature de fonction.

Les utilisateurs sont déconseillés d’utiliser ce **`__declspec`** modificateur, car des résultats inattendus peuvent se produire.

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
