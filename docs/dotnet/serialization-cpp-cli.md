---
title: Sérialisation (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: b2dfdcaf1a1f33e89d106d4529ffc9af2d08376b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988406"
---
# <a name="serialization-ccli"></a>Sérialisation (C++/CLI)

La sérialisation (processus de stockage de l’état d’un objet ou d’un membre sur un support permanent) de classes managées (y compris les champs ou les propriétés individuels) est prise en charge par les classes <xref:System.SerializableAttribute> et <xref:System.NonSerializedAttribute>.

## <a name="remarks"></a>Notes

Appliquez l’attribut personnalisé **SerializableAttribute** à une classe managée pour sérialiser la classe entière ou s’appliquer uniquement à des champs ou des propriétés spécifiques pour sérialiser des parties de la classe managée. Utilisez l’attribut personnalisé **NonSerializedAttribute** pour exempter les champs ou les propriétés d’une classe managée en cours de sérialisation.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Dans l’exemple suivant, la classe `MyClass` (et la propriété `m_nCount`) est marquée comme sérialisable. Toutefois, la propriété `m_nData` n’est pas sérialisée comme indiqué par l’attribut personnalisé non **sérialisé** :

### <a name="code"></a>Code

```cpp
// serialization_and_mcpp.cpp
// compile with: /LD /clr
using namespace System;

[ Serializable ]
public ref class MyClass {
public:
   int m_nCount;
private:
   [ NonSerialized ]
   int m_nData;
};
```

### <a name="comments"></a>Comments

Notez que les deux attributs peuvent être référencés à l’aide de leur nom « Short » (**Serializable** et **NonSerialized**). Cela est expliqué plus en détail dans [application des attributs](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
