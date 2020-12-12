---
description: 'En savoir plus sur : erreur du compilateur C3846'
title: Erreur du compilateur C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 13c9cb7a9dde3710cac31d8ee79fb148f8ff67bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255390"
---
# <a name="compiler-error-c3846"></a>Erreur du compilateur C3846

'Symbol' : impossible d’importer le symbole de’Assembly2 ', car’Symbol’a déjà été importé à partir d’un autre assembly’Assembly1 '

Impossible d’importer un symbole à partir d’un assembly référencé, car il a été importé précédemment à partir d’un assembly référencé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3846 :

```cpp
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

Puis compilez ce qui suit :

```cpp
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
