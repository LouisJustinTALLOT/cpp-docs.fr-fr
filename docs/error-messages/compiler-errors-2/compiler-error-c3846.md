---
title: Erreur du compilateur C3846 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f8b44661534dca1beb39c0407f882d41f1f503c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055128"
---
# <a name="compiler-error-c3846"></a>Erreur du compilateur C3846

'symbole' : Impossible d’importer le symbole de 'assembly2' : comme 'symbol' a déjà été importé à partir d’un autre assembly 'assembly1'

Un symbole n’a pas pu être importé à partir d’un assembly référencé, car il a été précédemment importé à partir d’un assembly référencé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3846 :

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

Et compilez ce code puis :

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
