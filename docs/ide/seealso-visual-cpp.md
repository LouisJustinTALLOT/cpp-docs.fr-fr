---
title: '&lt;seealso&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <seealso>
- seealso
dev_langs:
- C++
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a726a2fa1694fd346a6632fdc5e40bd53547fc8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33334306"
---
# <a name="ltseealsogt-visual-c"></a>&lt;seealso&gt; (Visual C++)
La balise \<seealso> vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi. Utilisez [\<see>](../ide/see-visual-cpp.md) pour spécifier un lien à partir de l’intérieur du texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `member`  
 Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.  Mettez le nom entre guillemets simples ou doubles.  
  
 Le compilateur vérifie que l’élément de code donné existe et qu’il résout `member` en nom d’élément dans le code XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.  
  
 Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [\<see>](../ide/see-visual-cpp.md).  
  
## <a name="remarks"></a>Notes  
 Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
 Pour obtenir un exemple d’utilisation de \<seealso>, consultez [\<summary>](../ide/summary-visual-cpp.md).  
  
 Le compilateur Visual C++ tente de résoudre les références cref en une seule passe via les commentaires de la documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un symbole non résolu est référencé dans un élément cref. Le commentaire XML pour la référence cref à B::Test est `<seealso cref="!:B::Test" />`, alors que la référence à A::Test est le code `<seealso cref="M:A.Test" />` bien formé.  
  
```  
// xml_seealso_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_seealso_tag.dll  
  
/// Text for class A.  
public ref struct A {  
   /// <summary><seealso cref="A::Test"/>  
   /// <seealso cref="B::Test"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void Test() {}  
};  
  
/// Text for class B.  
public ref struct B {  
   void Test() {}  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)