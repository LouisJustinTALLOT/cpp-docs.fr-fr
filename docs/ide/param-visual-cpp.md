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
ms.openlocfilehash: 01add77f68ac35b4c669391504461dd516b55d3d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33325381"
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
 Le texte de la balise \<param> s’affiche dans IntelliSense, dans [l’Explorateur d’objets](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) et dans le rapport web de commentaire de code.  
  
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