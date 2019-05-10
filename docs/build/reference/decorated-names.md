---
title: Noms décorés
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: e3950f79c4c88d031e04d0d145e0a03c9ebc0a37
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221792"
---
# <a name="decorated-names"></a>Noms décorés

Les fonctions, les données et les objets dans les programmes C et C++ sont représentés en interne par leurs noms décorés. Un *nom décoré* est une chaîne encodée créée par le compilateur pendant la compilation d’un objet, données ou définition de fonction. Il enregistre les conventions d'appel, les types, les paramètres de fonction et d'autres informations avec le nom. Cette décoration de nom, également appelée *troncage*, permet à l’éditeur de liens de trouver les fonctions et objets lors de la liaison d’un fichier exécutable.

Les conventions d’affectation de noms décorées ont changé dans différentes versions de Visual Studio et peuvent également être différentes selon l’architecture cible. Pour être lié correctement aux fichiers sources créés à l’aide de Visual Studio, C et C++ bibliothèques et DLL doivent être compilés en utilisant le même ensemble d’outils du compilateur, indicateurs et architecture cible. 

> [!NOTE]
> Bibliothèques générées avec Visual Studio 2015 peuvent être utilisées par les applications créées avec Visual Studio 2017 ou Visual Studio 2019.

##  <a name="Using"></a> À l’aide des noms décorés

Normalement, vous n'êtes pas tenu de connaître le nom décoré pour écrire du code pouvant être compilé et créer des liens avec succès. Les noms décorés sont un détail d'implémentation interne au compilateur et à l'éditeur de liens. Les outils peuvent habituellement gérer le nom dans sa forme non décorée. Cependant, un nom décoré est parfois nécessaire lorsque vous spécifiez un nom de fonction à l'éditeur de liens et à d'autres outils. Par exemple, pour faire correspondre des fonctions C++ surchargées, des membres d'espaces de noms, des constructeurs de classe, des destructeurs et des fonctions membres spéciales, vous devez spécifier le nom décoré. Pour plus d'informations sur les indicateurs d'option et d'autres situations qui nécessitent des noms décorés, consultez la documentation pour les outils et les options que vous utilisez.

Si vous modifiez le nom de la fonction, la classe, la convention d'appel, le type de retour ou n'importe quel paramètre, le nom décoré change également. Dans ce cas, vous devez obtenir le nouveau nom décoré et l'utiliser partout où le nom décoré est spécifié.

La décoration des noms est également importante lors de la liaison à du code écrit dans d'autres langages de programmation ou à l'aide d'autres compilateurs. Des compilateurs différents utilisent des conventions différentes de décoration des noms. Quand votre fichier exécutable est lié à du code écrit dans un autre langage, il convient d’apporter un soin particulier pour mettre en correspondance les noms exportés et importés et les conventions d’appel. Code en langage assembleur doit utiliser les noms MSVC décoré et les conventions d’appel à lier au code source écrit à l’aide de MSVC.

##  <a name="Format"></a> Format de C++ nom décoré

Un nom décoré pour une fonction C++ contient les informations suivantes :

- Nom de la fonction.

- Classe dont la fonction est membre, s'il s'agit d'une fonction membre. Celle-ci peut inclure la classe contenant la classe qui contient la fonction, etc.

- Espace de noms auquel la fonction appartient, si elle fait partie d'un espace de noms.

- Types des paramètres de la fonction.

- Convention d’appel.

- Type de retour de la fonction.

Les noms de fonction et de classe sont encodés dans le nom décoré. Le reste du nom décoré est un code qui a une signification interne uniquement pour le compilateur et l'éditeur de liens. Voici quelques exemples de noms C++ non décorés et décorés.

|Nom non décoré|Nom décoré|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

##  <a name="FormatC"></a> Format d’un C nom décoré

La forme de la décoration pour une fonction C dépend de la convention d’appel utilisée dans sa déclaration, comme l’indique le tableau suivant. Il s'agit également du format de décoration utilisé quand le code C++ est déclaré comme doté d'une liaison `extern "C"`. La convention d’appel par défaut est `__cdecl`. Notez que dans un environnement 64 bits, les fonctions ne sont pas décorées.

|Convention d'appel|Ornement|
|------------------------|----------------|
|`__cdecl`|Un trait de soulignement de début (**_**)|
|`__stdcall`|Un trait de soulignement de début (**_**) et signe arobase de fin (**\@**) suivi du nombre d’octets dans la liste de paramètres au format décimal|
|`__fastcall`|Début et de fin signes arobase (**\@**) suivie d’un nombre décimal qui représente le nombre d’octets dans la liste de paramètres|
|`__vectorcall`|Deux signes arobase de fin (**\@\@**) suivie d’un nombre décimal des octets dans la liste de paramètres|

##  <a name="Viewing"></a> Affichage des noms décorés

Vous pouvez obtenir la forme décorée du nom d'un symbole après avoir compilé le fichier source qui contient la définition ou le prototype des données, de l'objet ou de la fonction. Pour examiner les noms décorés dans votre programme, vous pouvez utiliser l'une des méthodes suivantes :

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Pour utiliser un listing pour afficher les noms décorés

1. Générez une liste en compilant le fichier source qui contient les données, objet, ou définition de fonction ou le prototype avec le [Type de fichier Listing](fa-fa-listing-file.md) option du compilateur définie sur Assembly avec Code Source (**/FA**).

   Par exemple, entrez `cl /c /FAs example.cpp` à une invite de commandes développeur pour générer un fichier listing, example.asm.

2. Dans le fichier listing obtenu, recherchez la ligne qui commence par PUBLIC et qui se termine par un point-virgule suivi du nom non décoré des données ou de la fonction. Le symbole entre PUBLIC et le point-virgule est le nom décoré.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Pour utiliser DUMPBIN pour afficher les noms décorés

1. Pour afficher les symboles exportés dans un fichier .obj ou .lib, entrez `dumpbin /symbols` `objfile` à une invite de commandes développeur.

2. Pour trouver la forme décorée d'un symbole, recherchez le nom non décoré entre parenthèses. Le nom décoré figure sur la même ligne, après une barre verticale (&#124;) caractère et avant le nom non décoré.

##  <a name="Undecorated"></a> Noms d’affichage non décoré

Vous pouvez utiliser undname.exe pour convertir un nom décoré vers sa forme non décorée. Cet exemple montre comment cela fonctionne :

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Voir aussi

[Outils de génération MSVC supplémentaires](c-cpp-build-tools.md)<br/>
[Utilisation d’extern pour spécifier la liaison](../../cpp/using-extern-to-specify-linkage.md)
