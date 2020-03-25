---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: 4626ba82d1d24582951bbffd8e6be687007d390f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178177"
---
# <a name="jitintrinsic"></a>jitintrinsic

Marque la fonction comme significative pour le CLR (Common Langage Runtime) 64 bits. Ceci est utilisé pour certaines fonctions dans les bibliothèques fournies par Microsoft.

## <a name="syntax"></a>Syntaxe

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Notes

**jitintrinsic** ajoute un MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) à une signature de fonction.

Les utilisateurs sont déconseillés d’utiliser ce modificateur de **__declspec** , car des résultats inattendus peuvent se produire.

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
