---
title: '&lt;list&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- list
- <list>
dev_langs:
- C++
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bff8e3588e31414f50cb6d150c0e8c9f2603586b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323977"
---
# <a name="ltlistgt-visual-c"></a>&lt;list&gt; (Visual C++)
Le bloc \<listheader> permet de définir la ligne d’en-tête d’une table ou d’une liste de définitions. Au moment de définir une table, il vous suffit de fournir une entrée pour le terme figurant dans l’en-tête.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 `term`  
 Terme à définir, qui est défini dans `description`.  
  
 `description`  
 Élément contenu dans une puce ou une liste numérotée ou définition d’un `term`.  
  
## <a name="remarks"></a>Notes  
 Chaque élément de la liste est spécifié avec un bloc \<item>. Au moment de créer une liste de définitions, vous devez spécifier à la fois `term` et `description`. Cependant, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.  
  
 Une liste ou une table peut comporter autant de blocs \<item> que nécessaire.  
  
 Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
  
```  
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
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)