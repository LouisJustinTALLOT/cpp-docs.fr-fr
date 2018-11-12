---
title: Avertissement du compilateur (niveau 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: d35c4143d5b90c7a6a49337931dad4ba73804f20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555625"
---
# <a name="compiler-warning-level-1-c4621"></a>Avertissement du compilateur (niveau 1) C4621

aucune forme suffixée de l’opérateur 'operator--' trouvée pour le type 'type', utilisez la forme préfixée

Il n’a aucun opérateur de décrémentation suffixée défini pour le type donné. Le compilateur a utilisé l’opérateur de préfixe surchargé.

Pour éviter cet avertissement, vous pouvez définir un opérateur `--` postfix. Créer une version à deux arguments de la `--` opérateur comme indiqué ci-dessous :

```
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