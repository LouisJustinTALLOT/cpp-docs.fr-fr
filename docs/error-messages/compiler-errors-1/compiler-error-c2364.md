---
description: 'En savoir plus sur : erreur du compilateur C2364'
title: Erreur du compilateur C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: 56d774a3ba681ec8cb3ab7bcf491766e30d6ba6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194875"
---
# <a name="compiler-error-c2364"></a>Erreur du compilateur C2364

'type' : type non conforme pour un attribut personnalisé

Les arguments nommés pour les attributs personnalisés sont limités aux constantes au moment de la compilation. Par exemple, les types intégraux (int, Char, etc.), System :: type ^ et System :: Object ^.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2364.

```cpp
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```
