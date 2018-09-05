---
title: '&lt;summary&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <summary>
- summary
dev_langs:
- C++
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47b7063dc9156e8feb41d447283ee457a13f1f4d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692300"
---
# <a name="ltsummarygt-visual-c"></a>&lt;summary&gt; (Visual C++)
La balise \<summary> doit être utilisée pour décrire un type ou un membre de type. Utilisez [\<remarks>](../ide/remarks-visual-cpp.md) pour ajouter des informations supplémentaires à une description de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `description`  
 Résumé de l’objet.  
  
## <a name="remarks"></a>Notes  
 Le texte de la balise \<summary> est la seule source d’informations sur le type dans IntelliSense et il est également affiché dans [l’Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) et dans le rapport web de commentaire de code.  
  
 Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
  
```  
// xml_summary_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_summary_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>  
   /// <seealso cref="MyClass::MyMethod2"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void MyMethod2() {}  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)