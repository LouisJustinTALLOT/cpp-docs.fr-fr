---
title: Utilisation de dllimport et dllexport dans les Classes C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 764ee2026e0ffcd112f202e0d400805c9df55e0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Utilisation de dllimport et dllexport dans les classes C++
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Vous pouvez déclarer des classes C++ avec la **dllimport** ou `dllexport` attribut. Ces formes impliquent que toute la classe soit importée ou exportée. Les classes exportées de cette façon sont appelées des classes exportables.  
  
 L'exemple suivant définit une classe exportable. Toutes ses fonctions membres et données statiques sont exportées :  
  
```  
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 Notez que l’utilisation explicite de la **dllimport** et `dllexport` attributs sur les membres d’une classe exportable est interdite.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> Classes de dllexport  
 Lorsque vous déclarez une classe `dllexport`, toutes ses fonctions membres et membres de données statiques sont exportés. Vous devez fournir les définitions de tous ces membres dans le même programme. Sinon, une erreur d'éditeur de liens est générée. La seule exception à cette règle s'applique aux fonctions virtuelles pures, pour lesquelles vous n'avez pas besoin de fournir de définitions explicites. Toutefois, étant donné qu'un destructeur d'une classe abstraite est toujours appelé par le destructeur de la classe de base, les destructeurs virtuels purs doivent toujours fournir une définition. Notez que ces règles sont identiques pour les classes non exportables.  
  
 Si vous exportez des données de classe de type ou des fonctions qui retournent des classes, veillez à exporter la classe.  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> Classes de dllimport  
 Lorsque vous déclarez une classe **dllimport**, toutes ses fonctions membres et les données membres statiques sont importés. Contrairement au comportement de **dllimport** et `dllexport` sur les types, les données membres static ne peut pas spécifier une définition dans le même programme dans lequel un **dllimport** classe est définie.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> Héritage et Classes exportables  
 Toutes les classes de base d'une classe exportable doivent être exportées. Sinon, un avertissement du compilateur est généré. De plus, tous les membres accessibles qui sont également des classes doivent être exportables. Cette règle autorise un `dllexport` classe hérite d’une **dllimport** (classe) et un **dllimport** classe hérite d’une `dllexport` classe (bien que ce dernier n’est pas recommandé). En règle générale, tout ce qui est accessible au client de la DLL (conformément aux règles d'accès C++) doit faire partie de l'interface exportable. Cela inclut les données membres privées référencées dans les fonctions inline.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> Importation/exportation de membres sélectifs  
 Étant donné que les fonctions membres et des données statiques dans une classe ont implicitement une liaison externe, vous pouvez les déclarer avec le **dllimport** ou `dllexport` d’attribut, à moins que la classe entière est exportée. Si la classe entière est importée ou exportée, la déclaration explicite de fonctions membres et les données en tant que **dllimport** ou `dllexport` est interdite. Si vous déclarez un membre de données statique dans une définition de classe comme `dllexport`, une définition doit apparaître quelque part dans le même programme (comme avec une liaison externe qui n'est pas de classe).  
  
 De même, vous pouvez déclarer les membres fonctions avec le **dllimport** ou `dllexport` attributs. Dans ce cas, vous devez fournir une définition `dllexport` à un emplacement du même programme.  
  
 Il est intéressant de noter plusieurs aspects importants concernant l'importation et l'exportation de membres sélectifs :  
  
-   L’importation/exportation de membres sélectifs permet principalement de fournir une version de l’interface de classe exportée qui est plus restrictive ; autrement dit, une version pour laquelle vous pouvez concevoir une DLL qui expose moins de fonctionnalités publiques et privées que ne le permet le langage. Cela permet également d'affiner l'interface exportable : lorsque vous savez que le client, par définition, ne peut pas accéder à certaines données privées, vous n'avez pas besoin d'exporter la classe entière.  
  
-   Si vous exportez une seule fonction virtuelle d'une classe, vous devez toutes les exporter ou fournir au moins les versions que le client peut utiliser directement.  
  
-   Si vous avez une classe dans laquelle vous utilisez l'importation/exportation de membres sélectifs avec des fonctions virtuelles, les fonctions doivent être dans l'interface exportable ou définies inline (visibles par le client).  
  
-   Si vous définissez un membre comme `dllexport` mais que vous ne l'incluez pas dans la définition de classe, une erreur de compilation est générée. Vous devez définir le membre dans l'en-tête de classe.  
  
-   Bien que la définition de membres de classe en tant que **dllimport** ou `dllexport` est autorisée, vous ne pouvez pas remplacer l’interface spécifiée dans la définition de classe.  
  
-   Si vous définissez une fonction membre dans un emplacement autre que le corps de la définition de classe dans laquelle vous l’avez déclarée, un avertissement est généré si la fonction est définie en tant que `dllexport` ou **dllimport** (si cette définition diffère de celui spécifié dans la déclaration de classe).  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)