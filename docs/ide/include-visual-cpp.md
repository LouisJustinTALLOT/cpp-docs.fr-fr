---
title: '&lt;include&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- include
- <include>
dev_langs:
- C++
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3cb07824ad5212f4174a6f19e3efa4549432455
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894446"
---
# <a name="ltincludegt-visual-c"></a>&lt;include&gt; (Visual C++)

La balise \<include> vous permet de faire référence à des commentaires dans un autre fichier qui décrivent les types et les membres dans votre code source. Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.  Par exemple, vous pouvez utiliser \<include> pour insérer des commentaires « d’éléments réutilisables » standard qui sont utilisés au sein de votre équipe ou société.

## <a name="syntax"></a>Syntaxe

```  
<include file='filename' path='tagpath' />
```  

#### <a name="parameters"></a>Paramètres

`filename`  
Nom du fichier contenant la documentation. Le nom de fichier peut être qualifié avec un chemin.  Mettez le nom entre guillemets simples ou doubles.  Le compilateur émet un avertissement s'il ne trouve pas `filename`.

`tagpath`  
Expression XPath valide qui sélectionne la collection de nœuds souhaitée contenue dans le fichier.

`name`  
Spécificateur de nom contenu dans la balise qui précède les commentaires ; `name` possède un `id`.

`id`  
ID de la balise qui précède les commentaires.  Mettez le nom entre guillemets simples ou doubles.

## <a name="remarks"></a>Notes

La balise \<include> utilise la syntaxe XML XPath. Reportez-vous à la documentation XPath pour savoir comment personnaliser votre utilisation de la balise \<include>.

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

Cet exemple comprend plusieurs fichiers. Le premier fichier, qui utilise \<include>, contient les commentaires de documentation suivants :

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

[Documentation XML](../ide/xml-documentation-visual-cpp.md)