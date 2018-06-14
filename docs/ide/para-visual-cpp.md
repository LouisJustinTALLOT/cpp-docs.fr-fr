---
title: '&lt;para&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <para>
- para
dev_langs:
- C++
helpviewer_keywords:
- <para> C++ XML tag
- para C++ XML tag
ms.assetid: 35f2a1b3-bc14-4f13-bcb0-c39ccbf74d59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ebf50e4672ee2a3398f6c484c42f8e36f231169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325115"
---
# <a name="ltparagt-visual-c"></a>&lt;para&gt; (Visual C++)
La balise \<para> est prévue pour une utilisation à l’intérieur d’une balise, telle que [ \<summary>](../ide/summary-visual-cpp.md), [\<remarks>](../ide/remarks-visual-cpp.md) ou [ \<returns>](../ide/returns-visual-cpp.md), et vous permet d’ajouter une structure au texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<para>content</para>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `content`  
 Texte du paragraphe.  
  
## <a name="remarks"></a>Notes  
 Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Consultez [\<summary>](../ide/summary-visual-cpp.md) pour obtenir un exemple d’utilisation de \<para>.  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)