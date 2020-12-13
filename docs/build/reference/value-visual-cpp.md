---
description: 'En savoir plus sur : &lt; valeur&gt;'
title: '&lt;valeur> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 110091607af7c973591384d44816f372f0d15b14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187024"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

La \<value> balise vous permet de décrire une propriété et des méthodes d’accesseur de propriété. Notez que lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement intégré Visual Studio, une [\<summary>](summary-visual-cpp.md) balise est ajoutée pour la nouvelle propriété. Vous devez ensuite ajouter manuellement une \<value> balise pour décrire la valeur représentée par la propriété.

## <a name="syntax"></a>Syntaxe

```
<value>property-description</value>
```

#### <a name="parameters"></a>Paramètres

*property-description*<br/>
Description de la propriété.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

## <a name="example"></a>Exemple

```cpp
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
