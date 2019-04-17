---
title: Erreur du compilateur C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 0f3eac1c232ef159d220a347d6b6dc3aed2fdd9a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771485"
---
# <a name="compiler-error-c3099"></a>Erreur du compilateur C3099

'mot clé' : utilisez [System::AttributeUsageAttribute] pour les attributs managés ; utilisez [Windows::Foundation::Metadata::AttributeUsageAttribute] pour les attributs WinRT

Utilisez <xref:System.AttributeUsageAttribute> pour déclarer **/CLR** attributs. Utilisez `Windows::Foundation::Metadata::AttributeUsageAttribute` pour déclarer des attributs Windows Runtime.

Pour plus d’informations sur les attributs/CLR, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md). Pour obtenir des attributs pris en charge dans Windows Runtime, consultez [Windows.Foundation.Metadata espace de noms](/uwp/api/windows.foundation.metadata)

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