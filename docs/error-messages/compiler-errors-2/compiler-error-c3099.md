---
title: Erreur du compilateur C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: e9a76fa2e0dc5602a88324cfd2fef85457ad7e99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512110"
---
# <a name="compiler-error-c3099"></a>Erreur du compilateur C3099

'mot clé' : utilisez [System::AttributeUsageAttribute] pour les attributs managés ; utilisez [Windows::Foundation::Metadata::AttributeUsageAttribute] pour les attributs WinRT

Utilisez <xref:System.AttributeUsageAttribute> pour déclarer **/CLR** attributs. Utilisez `Windows::Foundation::Metadata::AttributeUsageAttribute` pour déclarer des attributs Windows Runtime.

Pour plus d’informations sur les attributs/CLR, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md). Pour obtenir des attributs pris en charge dans Windows Runtime, consultez [Windows.Foundation.Metadata espace de noms](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3099 et montre comment la corriger.

```
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```