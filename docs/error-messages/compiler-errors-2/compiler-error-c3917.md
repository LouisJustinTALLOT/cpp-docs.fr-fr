---
description: 'En savoir plus sur : erreur du compilateur C3917'
title: Erreur du compilateur C3917
ms.date: 11/04/2016
f1_keywords:
- C3917
helpviewer_keywords:
- C3917
ms.assetid: a24cd0c9-262f-46e5-9488-1c01f945933d
ms.openlocfilehash: 3e30e93f650e1b835aafd6639687560aa7349c1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143934"
---
# <a name="compiler-error-c3917"></a>Erreur du compilateur C3917

'*propriété*' : style de déclaration de construction obsolète

Une définition de propriété ou d’événement a utilisé la syntaxe d’une version antérieure à Visual Studio 2005.

Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

## <a name="example"></a>Exemple

```cpp
// C3917.cpp
// compile with: /clr /c
public ref class  C {
private:
   int m_length;
public:
   C() {
      m_length = 0;
   }

   property int get_Length();   // C3917

   // The correct property definition:
   property int Length {
      int get() {
         return m_length;
      }

      void set( int i ) {
         m_length = i;
      }
   }
};
```
