---
title: Avertissement du compilateur (niveau 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 8ea4212eaddf14546827728b31299063021a959f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989636"
---
# <a name="compiler-warning-level-4-c4714"></a>Avertissement du compilateur (niveau 4) C4714

fonction’Function’marquée comme __forceinline non inline

La fonction donnée a été sélectionnée pour l’expansion Inline, mais le compilateur n’a pas effectué l’incorporation.

Bien que `__forceinline` soit une indication plus forte du compilateur que `__inline`, l’incorporation est toujours effectuée à la discrétion du compilateur, mais aucune heuristique n’est utilisée pour déterminer les avantages de l’incorporation de cette fonction.

Dans certains cas, le compilateur n’incorpore pas une fonction particulière pour des raisons mécaniques. Par exemple, le compilateur n’est pas inline :

- Une fonction si elle entraîne la combinaison de SEH et C++ Eh.

- Certaines fonctions avec des objets construits par copie passés par valeur quand-GX/EHs/EHa est activé.

- Les fonctions retournent un objet déroulable par valeur quand-GX/EHs/EHa est activé.

- Fonctionne avec un assembly inline lors de la compilation sans-og/Ox/O1/O2.

- Fonctions avec une liste d’arguments variable.

- Une fonction avec une instruction tryC++ (gestion des exceptions).

L’exemple suivant génère l’C4714 :

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
