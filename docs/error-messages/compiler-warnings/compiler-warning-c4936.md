---
title: Avertissement du compilateur C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: c6d54cf8b6704eec2a9e6af890c5c80c67106995
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165000"
---
# <a name="compiler-warning-c4936"></a>Avertissement du compilateur C4936

> ce __declspec est pris en charge uniquement lorsqu'il est compilé avec /clr ou /clr:pure

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

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
