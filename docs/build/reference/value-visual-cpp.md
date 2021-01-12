---
description: 'En savoir plus sur : &lt; valeur&gt;'
title: '&lt;valeur> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 5ebab554a33ff0d90b9306f3aec56b2552e18c5a
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126323"
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
