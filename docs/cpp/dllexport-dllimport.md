---
title: dllexport, dllimport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dllimport_cpp
- dllexport_cpp
dev_langs:
- C++
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a330ecf221d210134425c4bf39c17bac0f5006dc
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940532"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport
**Section spécifique à Microsoft**  
  
 Le **dllexport** et **dllimport** les attributs de classe de stockage sont des extensions spécifiques à Microsoft pour les langages C et C++. Vous pouvez les utiliser pour exporter et importer des fonctions, des données et des objets vers ou depuis une DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   __declspec( dllimport ) declarator  
   __declspec( dllexport ) declarator  
```  
  
## <a name="remarks"></a>Notes  
 Ces attributs définissent explicitement l'interface de la DLL à son client, qui peut être un fichier exécutable ou une autre DLL. Déclaration de fonctions comme **dllexport** élimine la nécessité d’un fichier de définition de module (.def), au moins en ce qui concerne la spécification de fonctions exportées. Le **dllexport** attribut remplace le **__export** mot clé.  
  
 Si une classe est marquée declspec(dllexport), les spécialisations des modèles de classe dans la hiérarchie de classes sont implicitement marquées comme declspec(dllexport). Cela signifie que les modèles de classe sont instanciés explicitement et que les membres de la classe doivent être définis.  
  
 **dllexport** d’une fonction expose la fonction avec son nom décoré. Pour les fonctions C++, cela inclut l'altération des noms. Pour les fonctions C ou les fonctions déclarées comme `extern "C"`, cela inclut la décoration propre à la plateforme basée sur la convention d'appel. Pour plus d’informations sur la décoration de nom dans le code C/C++, consultez [noms décorés](../build/reference/decorated-names.md). Aucune décoration de nom n'est appliquée aux fonctions C exportées ni aux fonctions `extern "C"` C++ à l'aide de la convention d'appel `__cdecl`.  
  
 Pour exporter un nom non décoré, vous pouvez établir un lien à l'aide d'un fichier de définition de module (.def) qui définit le nom non décoré dans une section EXPORTS. Pour plus d’informations, consultez [exportations](../build/reference/exports.md). Une autre façon d’exporter un nom non décoré consiste à utiliser un `#pragma comment(linker, "/export:alias=decorated_name")` directive dans le code source.  
  
 Lorsque vous déclarez **dllexport** ou **dllimport**, vous devez utiliser [étendu de syntaxe d’attribut](../cpp/declspec.md) et **__declspec** mot clé.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 Pour rendre votre code plus lisible, vous pouvez aussi utiliser des définitions de macros :  
  
```cpp  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllImport int j;  
DllExport int n;  
```  
  
 Pour plus d'informations, voir :  
  
-   [Définitions et déclarations](../cpp/definitions-and-declarations-cpp.md)  
  
-   [Définition de fonctions C++ incorporées avec dllexport et dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
-   [Règles générales et limitations](../cpp/general-rules-and-limitations.md)  
  
-   [Utilisation de dllimport et dllexport dans les classes C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__declspec](../cpp/declspec.md)   
 [Mots clés](../cpp/keywords-cpp.md)