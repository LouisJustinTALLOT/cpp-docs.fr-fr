---
description: 'En savoir plus sur : &lt; include&gt;'
title: '&lt;inclure des> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- <include>
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
ms.openlocfilehash: 577281b293fcca9b9b0b9491dd239240d435f32c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199777"
---
# <a name="ltincludegt"></a>&lt;include&gt;

La \<include> balise vous permet de faire référence aux commentaires d’un autre fichier qui décrivent les types et les membres de votre code source. Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.  Par exemple, vous pouvez utiliser \<include> pour insérer des commentaires « réutilisables » standard qui sont utilisés dans votre équipe ou votre entreprise.

## <a name="syntax"></a>Syntaxe

```
<include file='filename' path='tagpath' />
```

#### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier contenant la documentation. Le nom de fichier peut être qualifié avec un chemin.  Mettez le nom entre guillemets simples ou doubles.  Le compilateur émet un avertissement s'il ne trouve pas `filename`.

*tagpath*<br/>
Expression XPath valide qui sélectionne la collection de nœuds souhaitée contenue dans le fichier.

*name*<br/>
Spécificateur de nom contenu dans la balise qui précède les commentaires ; `name` possède un `id`.

*id*<br/>
ID de la balise qui précède les commentaires.  Mettez le nom entre guillemets simples ou doubles.

## <a name="remarks"></a>Notes

La \<include> balise utilise la syntaxe XML XPath. Reportez-vous à la documentation XPath pour savoir comment personnaliser à l’aide de \<include> .

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

## <a name="example"></a>Exemple

Cet exemple comprend plusieurs fichiers. Le premier fichier, qui utilise \<include> , contient les commentaires de documentation suivants :

```cpp
// xml_include_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_include_tag.dll

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />
public ref class Test {
   void TestMethod() {
   }
};

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />
public ref class Test2 {
   void Test() {
   }
};
```

Le deuxième, xml_include_tag.doc, contient les commentaires de la documentation suivants :

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>Sortie du programme

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>t2</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
