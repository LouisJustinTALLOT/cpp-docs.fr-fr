---
title: Erreur du compilateur C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 4e5d5335717ec77c61069ad08e209f9e1851dc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205307"
---
# <a name="compiler-error-c2441"></a>Erreur du compilateur C2441

> '*variable*' : un symbole déclaré avec __declspec (processus) doit être const en mode/clr : pure

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Par défaut, les variables sont par domaine d’application sous **/clr : pure**. Une variable marquée `__declspec(process)` sous **/clr : pure** est sujette aux erreurs si elle est modifiée dans un domaine d’application et lue dans une autre.

Par conséquent, le compilateur applique les variables par processus `const` sous **/clr : pure**, ce qui les rend accessibles en lecture seule dans tous les domaines d’application.

Pour plus d’informations, consultez [Process](../../cpp/process.md) et [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
