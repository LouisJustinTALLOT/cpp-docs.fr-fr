---
title: Avertissement du compilateur C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: bbb69cccbf93be6e97d13db5008780f57e63f9da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280852"
---
# <a name="compiler-warning-c4936"></a>Avertissement du compilateur C4936

> ce __declspec est pris en charge uniquement lorsqu'il est compilé avec /clr ou /clr:pure

## <a name="remarks"></a>Notes

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Un modificateur `__declspec` a été utilisé, mais ce modificateur `__declspec` est valide uniquement quand il est compilé avec l’une des options [/clr](../../build/reference/clr-common-language-runtime-compilation.md) .

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

C4936 est toujours émis en tant qu’erreur.  Vous pouvez désactiver C4936 avec le pragma [warning](../../preprocessor/warning.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4936 :

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```