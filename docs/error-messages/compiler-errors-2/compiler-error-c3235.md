---
description: 'En savoir plus sur : erreur du compilateur C3235'
title: Erreur du compilateur C3235
ms.date: 11/04/2016
f1_keywords:
- C3235
helpviewer_keywords:
- C3235
ms.assetid: 0554d6c7-e1dc-4c99-8934-cbcf491c8203
ms.openlocfilehash: 5e478e9104599f833d3f63abb042660816425028
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311901"
---
# <a name="compiler-error-c3235"></a>Erreur du compilateur C3235

'specialization' : la spécialisation explicite ou partielle d’une classe générique n’est pas autorisée

Les classes génériques ne peuvent pas être utilisées pour les spécialisations explicites ou partielles.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3235.

```cpp
// C3235.cpp
// compile with: /clr
generic<class T>
public ref class C {};

generic<>
public ref class C<int> {};   // C3235 Remove this specialization to resolve this error.
```
