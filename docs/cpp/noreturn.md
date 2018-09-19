---
title: noreturn | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133fc70c5c2b8bb8f794746c1d5ca11be97b817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031039"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Cela **__declspec** attribut indique au compilateur qu’une fonction ne retourne pas. Par conséquent, le compilateur sait que le code qui suit un appel à une **__declspec (noreturn)** (fonction) est inaccessible.

Si le compilateur recherche une fonction avec un chemin d’accès au contrôle qui ne retourne pas de valeur, il génère un avertissement (C4715) ou le message d’erreur (C2202). Si le chemin d’accès de contrôle ne peut pas être atteint en raison d’une fonction qui ne retourne jamais, vous pouvez utiliser **__declspec (noreturn)** pour éviter cet avertissement ou erreur.

> [!NOTE]
>  Ajout de **__declspec (noreturn)** à une fonction qui est censée retourner peut entraîner un comportement non défini.

## <a name="example"></a>Exemple

Dans l’exemple suivant, le **else** clause ne contient pas une instruction return.  Déclaration `fatal` comme **__declspec (noreturn)** permet d’éviter une erreur ou un message d’avertissement.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)