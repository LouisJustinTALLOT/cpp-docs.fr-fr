---
title: Avertissement du compilateur (niveau 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 4126a1267b41cdf9c0161c7e85a9057b2a301d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401967"
---
# <a name="compiler-warning-level-3-c4398"></a>Avertissement du compilateur (niveau 3) C4398

> «*variable*' : objet global par processus ne peuvent ne pas fonctionne correctement avec plusieurs appdomains ; utilisez __declspec

## <a name="remarks"></a>Notes

Une fonction virtuelle avec [__clrcall](../../cpp/clrcall.md) convention d’appel dans un type natif provoque la création d’une application vtable par domaine. Une variable de ce type ne peut pas résoudre correctement lorsqu’il est utilisé dans plusieurs domaines d’application.

Vous pouvez résoudre cet avertissement en marquant explicitement la variable `__declspec(appdomain)`. Dans les versions de Visual Studio antérieures à Visual Studio 2017, vous pouvez résoudre cet avertissement en compilant avec **/CLR : pure**, ce qui rend les variables globales par appdomain par défaut. Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [domaines d’Application et Visual C++](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4398.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```