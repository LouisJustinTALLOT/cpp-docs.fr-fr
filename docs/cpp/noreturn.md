---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: a30840aa0556a7324ba24c0f2aaec57dea88d082
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367853"
---
# <a name="noreturn"></a>noreturn

**Microsoft Spécifique**

Cet attribut **__declspec** indique au compilateur qu’une fonction ne revient pas. En conséquence, le compilateur sait que le code suivant un appel à une fonction **__declspec (noreturn)** est inaccessible.

Si le compilateur recherche une fonction avec un chemin d’accès au contrôle qui ne retourne pas de valeur, il génère un avertissement (C4715) ou le message d’erreur (C2202). Si la voie de contrôle ne peut pas être atteinte en raison d’une fonction qui ne revient jamais, vous pouvez utiliser **__declspec (noreturn)** pour empêcher cet avertissement ou erreur.

> [!NOTE]
> L’ajout **de __declspec (noreturn)** à une fonction qui devrait revenir peut entraîner un comportement indéfini.

## <a name="example"></a>Exemple

Dans l’échantillon suivant, **l’autre** clause ne contient pas de déclaration de déclaration.  Déclarer `fatal` comme **__declspec (noreturn)** évite une erreur ou un message d’avertissement.

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

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
