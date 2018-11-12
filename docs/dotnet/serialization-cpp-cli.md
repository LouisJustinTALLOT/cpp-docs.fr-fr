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
ms.openlocfilehash: 74810328d654787be46794a31d857eb3fd0731ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478141"
---
# <a name="serialization-ccli"></a>Sérialisation (C++/CLI)

Sérialisation (processus de stockage de l’état d’un objet ou un membre à un support permanent) des classes managées (y compris les différents champs ou propriétés) est prise en charge par le <xref:System.SerializableAttribute> et <xref:System.NonSerializedAttribute> classes.

## <a name="remarks"></a>Notes

Appliquer le **SerializableAttribute** attribut personnalisé à une classe managée pour sérialiser la classe entière ou de s’appliquent uniquement à certains champs ou propriétés à sérialiser des parties de la classe managée. Utilisez le **NonSerializedAttribute** des attributs personnalisés pour exempter des champs ou propriétés d’une classe managée ne soient sérialisés.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Dans l’exemple suivant, la classe `MyClass` (et la propriété `m_nCount`) est marqué comme sérialisable. Toutefois, le `m_nData` propriété n’est pas sérialisée comme indiqué par le **NonSerialized** attribut personnalisé :

### <a name="code"></a>Code

```
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

Notez que les deux attributs peuvent être référencés à l’aide de leur « nom court » (**Serializable** et **NonSerialized**). Cela est expliqué plus en détails dans [application des attributs](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)