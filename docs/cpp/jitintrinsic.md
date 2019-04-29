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
ms.openlocfilehash: 9e726413f0bbfbd9d6affa348777c995c51283a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245512"
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