---
title: Utilisation de dllimport et dllexport dans les classes C++
ms.date: 11/04/2016
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
ms.openlocfilehash: c0a2c96a37f58c956976980beafd5ecbed4d1318
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365121"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Utilisation de dllimport et dllexport dans les classes C++

**Microsoft Spécifique**

Vous pouvez déclarer les cours de C avec **l’attribut dllimport** ou **dllexport.** Ces formes impliquent que toute la classe soit importée ou exportée. Les classes exportées de cette façon sont appelées des classes exportables.

L'exemple suivant définit une classe exportable. Toutes ses fonctions membres et données statiques sont exportées :

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Notez que l’utilisation explicite des attributs **dllimport** et **dllexport** sur les membres d’une classe exportable est interdite.

## <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>Cours dllexport

Lorsque vous déclarez un **dllexport de**classe, toutes ses fonctions membres et les membres de données statiques sont exportés. Vous devez fournir les définitions de tous ces membres dans le même programme. Sinon, une erreur d'éditeur de liens est générée. La seule exception à cette règle s'applique aux fonctions virtuelles pures, pour lesquelles vous n'avez pas besoin de fournir de définitions explicites. Toutefois, étant donné qu'un destructeur d'une classe abstraite est toujours appelé par le destructeur de la classe de base, les destructeurs virtuels purs doivent toujours fournir une définition. Notez que ces règles sont identiques pour les classes non exportables.

Si vous exportez des données de classe de type ou des fonctions qui retournent des classes, veillez à exporter la classe.

## <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>Cours dllimport

Lorsque vous déclarez un **dllimport de**classe, toutes ses fonctions membres et les membres de données statiques sont importés. Contrairement au comportement du **dllimport** et **du dllexport** sur les types non-class, les membres de données statiques ne peuvent pas spécifier une définition dans le même programme dans lequel une classe **de dllimport** est définie.

## <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Héritage et classes exportables

Toutes les classes de base d'une classe exportable doivent être exportées. Sinon, un avertissement du compilateur est généré. De plus, tous les membres accessibles qui sont également des classes doivent être exportables. Cette règle permet à une classe **de dllexport** d’hériter d’une classe **de dllimport,** et une classe **de dllimport** d’hériter d’une classe **de dllexport** (bien que ce dernier ne soit pas recommandé). En règle générale, tout ce qui est accessible au client de la DLL (conformément aux règles d'accès C++) doit faire partie de l'interface exportable. Cela inclut les données membres privées référencées dans les fonctions inline.

## <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Importation/Exportation sélective des membres

Étant donné que les fonctions des membres et les données statiques au sein d’une classe ont implicitement un lien externe, vous pouvez les déclarer avec **l’attribut dllimport** ou **dllexport,** à moins que toute la classe ne soit exportée. Si toute la classe est importée ou exportée, la déclaration explicite des fonctions et des données des membres sous **forme de dllimport** ou **de dllexport** est interdite. Si vous déclarez un membre de données statiques dans une définition de classe comme **dllexport**, une définition doit se produire quelque part dans le même programme (comme avec la liaison externe non class).

De même, vous pouvez déclarer les fonctions des membres avec les attributs **dllimport** ou **dllexport.** Dans ce cas, vous devez fournir une définition **dllexport** quelque part dans le même programme.

Il est intéressant de noter plusieurs aspects importants concernant l'importation et l'exportation de membres sélectifs :

- L'importation/exportation de membres sélectifs permet principalement de fournir une version de l'interface de classe exportée qui est plus restrictive ; autrement dit, une version pour laquelle vous pouvez concevoir une DLL qui expose moins de fonctionnalités publiques et privées que ne le permet le langage. Cela permet également d'affiner l'interface exportable : lorsque vous savez que le client, par définition, ne peut pas accéder à certaines données privées, vous n'avez pas besoin d'exporter la classe entière.

- Si vous exportez une seule fonction virtuelle d'une classe, vous devez toutes les exporter ou fournir au moins les versions que le client peut utiliser directement.

- Si vous avez une classe dans laquelle vous utilisez l'importation/exportation de membres sélectifs avec des fonctions virtuelles, les fonctions doivent être dans l'interface exportable ou définies inline (visibles par le client).

- Si vous définissez un membre comme **dllexport** mais ne l’incluez pas dans la définition de classe, une erreur de compilateur est générée. Vous devez définir le membre dans l'en-tête de classe.

- Bien que la définition des membres de la classe comme **dllimport** ou **dllexport** soit autorisée, vous ne pouvez pas remplacer l’interface spécifiée dans la définition de classe.

- Si vous définissez une fonction de membre dans un endroit autre que le corps de la définition de classe dans laquelle vous l’avez déclarée, un avertissement est généré si la fonction est définie comme **dllexport** ou **dllimport** (si cette définition diffère de celle spécifiée dans la déclaration de classe).

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
