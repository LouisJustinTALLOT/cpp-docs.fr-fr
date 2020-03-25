---
title: Erreur du compilateur C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 7ef22711884dabb83efa8c7ebfdb7648316c12ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205411"
---
# <a name="compiler-error-c2435"></a>Erreur du compilateur C2435

> '*var*' : l’initialisation dynamique requiert un CRT managé, impossible de compiler avec/clr : safe

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

L’initialisation d’une variable de domaine par application globale nécessite que la bibliothèque CRT soit compilée avec `/clr:pure`, ce qui ne produit pas d’image vérifiable.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2435 :

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```
