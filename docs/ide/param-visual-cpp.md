---
title: '&lt;param&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69e2950fcc0b29fb819445f3216ef262a2657e4a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686419"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)
La balise \<param> doit être utilisée dans le commentaire de la déclaration d’une méthode pour décrire l’un des paramètres de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `name`  
 Nom d’un paramètre de méthode.  Mettez le nom entre guillemets simples ou doubles.  Le compilateur émet un avertissement s'il ne trouve pas `name`.  
  
 `description`  
 Description du paramètre.  
  
## <a name="remarks"></a>Notes  
 Le texte de la balise \<param> s’affiche dans IntelliSense, dans [l’Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) et dans le rapport web de commentaire de code.  
  
 Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)