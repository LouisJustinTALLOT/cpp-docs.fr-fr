---
description: 'En savoir plus sur : erreur du compilateur C2435'
title: Erreur du compilateur C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: d0ab5d8c7c45c9636a5e48acc17d3ac379c755a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189936"
---
# <a name="compiler-error-c2435"></a>Erreur du compilateur C2435

> '*var*' : l’initialisation dynamique requiert un CRT managé, impossible de compiler avec/clr : safe

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

L’initialisation d’une variable de domaine par application globale nécessite la compilation du CRT avec `/clr:pure` , qui ne produit pas d’image vérifiable.

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
