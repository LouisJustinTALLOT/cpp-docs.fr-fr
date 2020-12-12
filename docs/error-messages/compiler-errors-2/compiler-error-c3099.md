---
description: 'En savoir plus sur : erreur du compilateur C3099'
title: Erreur du compilateur C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: d065edd58df1e9196dc6aa31cfd4fb263f062f1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116221"
---
# <a name="compiler-error-c3099"></a>Erreur du compilateur C3099

'mot clé' : utilisez [System::AttributeUsageAttribute] pour les attributs managés ; utilisez [Windows::Foundation::Metadata::AttributeUsageAttribute] pour les attributs WinRT

Utilisez <xref:System.AttributeUsageAttribute> pour déclarer des attributs **/CLR** . Utilisez `Windows::Foundation::Metadata::AttributeUsageAttribute` pour déclarer des attributs Windows Runtime.

Pour plus d’informations sur les attributs/CLR, consultez [attributs définis par l’utilisateur](../../extensions/user-defined-attributes-cpp-component-extensions.md). Pour obtenir les attributs pris en charge dans Windows Runtime, consultez [espace de noms Windows. Foundation. Metadata](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3099 et montre comment la corriger.

```cpp
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```
