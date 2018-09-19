---
title: Erreur du compilateur C2297 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2297
dev_langs:
- C++
helpviewer_keywords:
- C2297
ms.assetid: 65849fe5-17e1-4b7e-b50c-f508b05ddaa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21c2ed8637dd93d6b7b8f5559ca20433e64ecea9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071800"
---
# <a name="compiler-error-c2297"></a>Erreur du compilateur C2297

'opérateur' : opérande droit incorrect

L’opérande droit utilisé avec `operator` n’est pas valide.

Par exemple, le compilateur peut afficher une déclaration, où vous aviez l’intention un appel de fonction.

L’exemple suivant génère l’erreur C2297 :

```
// C2297.cpp
struct MyStruct {
   struct Help {
      Help(float f) : m_f(f) {}
      float m_f;
   };

   MyStruct(const Help &h) : m_f(h.m_f) {}

   MyStruct(float f) : m_f(f) {}

   MyStruct operator*(const MyStruct &f1) const {
      return MyStruct(m_f * f1.m_f);
   }

private:
   float m_f;
};

int main() {
   float f1 = 1.0f;

   MyStruct m_MyStruct1 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct1 = MyStruct::Help( f1 );

   MyStruct m_MyStruct2 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct2 = MyStruct::Help( f1 );

   MyStruct m_MyStruct3 = m_MyStruct1 * m_MyStruct2;   // C2297
}
```