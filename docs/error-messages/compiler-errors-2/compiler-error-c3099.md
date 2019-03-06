---
title: Erreur du compilateur C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: beaa34bb9bed4824383cdad32c6bfd0aea19f6b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418571"
---
# <a name="compiler-error-c3099"></a>Erreur du compilateur C3099

'mot clé' : utilisez [System::AttributeUsageAttribute] pour les attributs managés ; utilisez [Windows::Foundation::Metadata::AttributeUsageAttribute] pour les attributs WinRT

Utilisez <xref:System.AttributeUsageAttribute> pour déclarer **/CLR** attributs. Utilisez `Windows::Foundation::Metadata::AttributeUsageAttribute` pour déclarer des attributs Windows Runtime.

Pour plus d’informations sur les attributs/CLR, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md). Pour obtenir des attributs pris en charge dans Windows Runtime, consultez [Windows.Foundation.Metadata espace de noms](/uwp/api/windows.foundation.metadata)

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