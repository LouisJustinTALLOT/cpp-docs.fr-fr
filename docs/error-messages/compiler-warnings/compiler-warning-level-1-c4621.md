---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4621'
title: Avertissement du compilateur (niveau 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: 72e4adbb45488b200ff67f1d0b225591f9ea1a6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281468"
---
# <a name="compiler-warning-level-1-c4621"></a>Avertissement du compilateur (niveau 1) C4621

aucune forme suffixée de’operator--'trouvée pour le type’type', à l’aide d’une forme de préfixe

Aucun opérateur de décrémentation postfix n’a été défini pour le type donné. Le compilateur a utilisé l’opérateur de préfixe surchargé.

Pour éviter cet avertissement, vous pouvez définir un opérateur `--` postfix. Créez une version à deux arguments de l' `--` opérateur, comme indiqué ci-dessous :

```cpp
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   --a;
   a--;   // C4621
}
```
