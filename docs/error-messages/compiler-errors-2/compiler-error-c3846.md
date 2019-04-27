---
title: Erreur du compilateur C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 788f03e4364404ad5c30b7edcba8b743c7f201ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152421"
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
