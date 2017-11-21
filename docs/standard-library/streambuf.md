---
title: '&lt;streambuf&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <streambuf>
dev_langs: C++
helpviewer_keywords: streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 19be7e9ce24003dd2c00ddb0f9d9a1f5e92a5363
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;
Incluez l’en-tête standard iostreams \<streambuf> pour définir la classe de modèle [basic_streambuf](../standard-library/basic-streambuf-class.md), qui est essentielle au fonctionnement des classes iostreams. Cet en-tête est généralement inclus pour vous par l'un des autres en-tête iostream ; vous devez rarement l'inclure directement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <streambuf>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Spécialisation de `basic_streambuf` qui utilise `char` comme paramètres du modèle.|  
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Spécialisation de `basic_streambuf` qui utilise `wchar_t` comme paramètres du modèle.|  
  
### <a name="classes"></a>Classes  
  
|||  
|-|-|  
|[basic_streambuf, classe](http://msdn.microsoft.com/en-us/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|La classe de modèle décrit une classe de base abstraite pour dériver une mémoire tampon de flux qui contrôle la transmission des éléments depuis et vers une représentation spécifique d'un flux.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)   
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream, programmation](../standard-library/iostream-programming.md)   
 [iostreams, conventions](../standard-library/iostreams-conventions.md)



