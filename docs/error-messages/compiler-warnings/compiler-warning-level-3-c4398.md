---
title: Avertissement du compilateur (niveau 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 041bf9f6bfce17b16f301604bb8706be30095c13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198664"
---
# <a name="compiler-warning-level-3-c4398"></a>Avertissement du compilateur (niveau 3) C4398

> '*variable*' : un objet global par processus peut ne pas fonctionner correctement avec plusieurs AppDomains ; envisagez d’utiliser __declspec (AppDomain)

## <a name="remarks"></a>Notes

Une fonction virtuelle avec [__clrcall](../../cpp/clrcall.md) Convention d’appel dans un type natif provoque la création d’un vtable par domaine d’application. Une telle variable peut ne pas être correcte correctement lorsqu’elle est utilisée dans plusieurs domaines d’application.

Vous pouvez résoudre cet avertissement en marquant explicitement la variable `__declspec(appdomain)`. Dans les versions de Visual Studio antérieures à Visual Studio 2017, vous pouvez résoudre cet avertissement en compilant avec **/clr : pure**, qui crée par défaut des variables globales par AppDomain. L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Pour plus d’informations, consultez [AppDomain](../../cpp/appdomain.md) et [domaines d’application C++et Visual ](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4398.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```
