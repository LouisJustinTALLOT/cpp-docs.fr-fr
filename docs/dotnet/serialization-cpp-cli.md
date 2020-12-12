---
description: 'En savoir plus sur : sérialisation (C++/CLI)'
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
ms.openlocfilehash: 1524ed5d4a000d2006f6f830b1d82119d170c3b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164599"
---
# <a name="serialization-ccli"></a>Sérialisation (C++/CLI)

La sérialisation (processus de stockage de l’état d’un objet ou d’un membre sur un support permanent) de classes managées (y compris des champs ou des propriétés individuels) est prise en charge par les <xref:System.SerializableAttribute> <xref:System.NonSerializedAttribute> classes et.

## <a name="remarks"></a>Notes

Appliquez l’attribut personnalisé **SerializableAttribute** à une classe managée pour sérialiser la classe entière ou s’appliquer uniquement à des champs ou des propriétés spécifiques pour sérialiser des parties de la classe managée. Utilisez l’attribut personnalisé **NonSerializedAttribute** pour exempter les champs ou les propriétés d’une classe managée en cours de sérialisation.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Dans l’exemple suivant, la classe `MyClass` (et la propriété `m_nCount` ) est marquée comme sérialisable. Toutefois, la `m_nData` propriété n’est pas sérialisée comme indiqué par l’attribut personnalisé non **sérialisé** :

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

### <a name="comments"></a>Commentaires

Notez que les deux attributs peuvent être référencés à l’aide de leur nom « Short » (**Serializable** et **NonSerialized**). Cela est expliqué plus en détail dans [application des attributs](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
