---
description: 'En savoir plus sur : erreur du compilateur C3106'
title: Erreur du compilateur C3106
ms.date: 11/04/2016
f1_keywords:
- C3106
helpviewer_keywords:
- C3106
ms.assetid: 39d97a32-0905-4702-87d3-7f8ce473fb93
ms.openlocfilehash: 59e0544a05362584836c4cae60d0fc3d3cd920d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116078"
---
# <a name="compiler-error-c3106"></a>Erreur du compilateur C3106

'Attribute' : les arguments sans nom doivent précéder les arguments nommés

Les arguments sans nom doivent être passés à un attribut avant les arguments nommés.

Pour plus d'informations, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3106.

```cpp
// C3106.cpp
// compile with: /c
[module(name="MyLib", dll)];   // C3106
[module(dll, name="MyLib")];   // OK
```
