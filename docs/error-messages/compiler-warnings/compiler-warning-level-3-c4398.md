---
title: Compilateur avertissement (niveau 3) C4398 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c38ade6b75242fdd5144481e3415e914cb6773c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704612"
---
# <a name="compiler-warning-level-3-c4398"></a>Avertissement du compilateur (niveau 3) C4398

> '*variable*' : objet global par processus ne peut pas fonctionner correctement avec plusieurs appdomains ; utilisez __declspec(appdomain)

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