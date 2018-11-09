---
title: '&lt;value&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 84a19c96e3e7024dbb891c6bde91646d4731b2be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599288"
---
# <a name="ltvaluegt-visual-c"></a>&lt;value&gt; (Visual C++)

La balise \<value> vous permet de décrire une propriété et des méthodes d’accesseur de propriété. Notez que, quand vous ajoutez une propriété avec un Assistant Code dans l’environnement de développement intégré (IDE) de Visual Studio, cela ajoute une balise [\<summary>](../ide/summary-visual-cpp.md) pour la nouvelle propriété. Vous devez ensuite ajouter manuellement une balise \<value> pour décrire la valeur représentée par la propriété.

## <a name="syntax"></a>Syntaxe

```
<value>property-description</value>
```

#### <a name="parameters"></a>Paramètres

*property-description*<br/>
Description de la propriété.

## <a name="remarks"></a>Notes

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```
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

[Documentation XML](../ide/xml-documentation-visual-cpp.md)