---
description: 'En savoir plus sur : &lt; List &gt; et &lt; listheader (&gt;'
title: '&lt;List> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- list
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: cb34e4361c68be58297d0f2e063974a2f94de991
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199205"
---
# <a name="ltlistgt-and-ltlistheadergt"></a>&lt;liste &gt; et &lt; listheader (&gt;

Le \<listheader> bloc est utilisé pour définir la ligne d’en-tête d’une table ou d’une liste de définitions. Au moment de définir une table, il vous suffit de fournir une entrée pour le terme figurant dans l’en-tête.

## <a name="syntax"></a>Syntaxe

```xml
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>Paramètres

*terme*<br/>
Terme à définir, qui est défini dans `description`.

*description*<br/>
Élément contenu dans une puce ou une liste numérotée ou définition d’un `term`.

## <a name="remarks"></a>Notes

Chaque élément de la liste est spécifié avec un \<item> bloc. Au moment de créer une liste de définitions, vous devez spécifier à la fois `term` et `description`. Cependant, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.

Une liste ou une table peut avoir autant de \<item> blocs que nécessaire.

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

## <a name="example"></a>Exemple

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
