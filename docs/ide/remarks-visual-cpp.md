---
title: '&lt;remarks&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- remarks
- <remarks>
dev_langs:
- C++
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 409f10dffdf6816f3ff0ab4e71060c9bcb6eaf9f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684210"
---
# <a name="ltremarksgt-visual-c"></a>&lt;remarks&gt; (Visual C++)
La balise \<remarks> permet d’ajouter des informations sur un type en complétant les informations spécifiées par [\<summary>](../ide/summary-visual-cpp.md). Ces informations sont affichées dans [l’Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) et dans le rapport web de commentaire de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `description`  
 Description du membre.  
  
## <a name="remarks"></a>Notes  
 Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
  
```  
// xml_remarks_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_remarks_tag.dll  
  
using namespace System;  
  
/// <summary>  
/// You may have some primary information about this class.  
/// </summary>  
/// <remarks>  
/// You may have some additional information about this class.  
/// </remarks>  
public ref class MyClass {};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)