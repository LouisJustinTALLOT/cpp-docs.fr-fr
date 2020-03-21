---
title: Déclarations et définitions (C++)
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: 7aa9e07a471ed5a32ecc8f13690f1a1bf08b655f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077213"
---
# <a name="declarations-and-definitions-c"></a>Déclarations et définitions (C++)

Un C++ programme se compose de différentes entités, telles que des variables, des fonctions, des types et des espaces de noms. Chacune de ces entités doit être *déclarée* avant de pouvoir être utilisée. Une déclaration spécifie un nom unique pour l’entité, ainsi que des informations sur son type et d’autres caractéristiques. C++ Le point auquel un nom est déclaré est le point auquel il devient visible par le compilateur. Vous ne pouvez pas faire référence à une fonction ou une classe qui est déclarée à un point ultérieur dans l’unité de compilation. Les variables doivent être déclarées aussi près que possible avant le point où elles sont utilisées.

L’exemple suivant illustre certaines déclarations :

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

À la ligne 5, la fonction `main` est déclarée. À la ligne 7, une variable **const** nommée `pi` est déclarée et *initialisée*. Sur la ligne 8, un `i` entier est déclaré et initialisé avec la valeur produite par la fonction `f`. Le nom `f` est visible par le compilateur en raison de la *déclaration anticipée* à la ligne 3.

À la ligne 9, une variable nommée `obj` de type `C` est déclarée. Toutefois, cette déclaration génère une erreur, car `C` n’est pas déclarée jusqu’à une date ultérieure dans le programme et n’est pas déclarée par progression. Pour corriger l’erreur, vous pouvez déplacer l’intégralité de la *définition* de `C` avant `main` ou ajouter une déclaration de transfert pour celle-ci. Ce comportement est différent de celui des autres langages tels que C#, dans lesquels les fonctions et les classes peuvent être utilisées avant leur point de déclaration dans un fichier source.

À la ligne 10, une variable nommée `str` de type `std::string` est déclarée. Le nom `std::string` est visible, car il est introduit dans le [fichier d’en-tête](header-files-cpp.md) `string` qui est fusionné dans le fichier source à la ligne 1. `std` est l’espace de noms dans lequel la classe `string` est déclarée.

À la ligne 11, une erreur est générée, car le nom `j` n’a pas été déclaré. Une déclaration doit fournir un type, contrairement à d’autres langages tels que javaScript. À la ligne 12, le mot clé `auto` est utilisé, ce qui indique au compilateur de déduire le type de `k` en fonction de la valeur avec laquelle il est initialisé. Dans ce cas, le compilateur choisit `int` pour le type.  

## <a name="declaration-scope"></a>Portée de la déclaration

Le nom introduit par une déclaration est valide dans l' *étendue* où la déclaration se produit. Dans l’exemple précédent, les variables déclarées à l’intérieur de la fonction `main` sont des *variables locales*. Vous pouvez déclarer une autre variable nommée `i` en dehors de main, au niveau de la *portée globale*, et il s’agit d’une entité complètement distincte. Toutefois, une telle duplication des noms peut entraîner une confusion et des erreurs de programmeur, et doit être évitée. À la ligne 21, la classe `C` est déclarée dans la portée de l’espace de noms `N`. L’utilisation des espaces de noms permet d’éviter les *conflits de noms*. La C++ plupart des noms de bibliothèque standard sont déclarés dans l’espace de noms `std`. Pour plus d’informations sur la façon dont les règles d’étendue interagissent avec les déclarations, consultez [scope](../cpp/scope-visual-cpp.md).

## <a name="definitions"></a>Définitions

Certaines entités, y compris les fonctions, les classes, les énumérations et les variables constantes, doivent être définies en plus d’être déclarées. Une *définition* fournit au compilateur toutes les informations dont il a besoin pour générer le code machine lorsque l’entité est utilisée ultérieurement dans le programme. Dans l’exemple précédent, la ligne 3 contient une déclaration pour la fonction `f` mais la *définition* de la fonction est fournie dans les lignes 15 à 18. À la ligne 21, la classe `C` est déclarée et définie (bien que, comme défini, la classe n’effectue aucune action). Une variable constante doit être définie, en d’autres termes, une valeur qui lui est assignée, dans la même instruction que celle dans laquelle elle est déclarée. Une déclaration d’un type intégré tel que `int` est automatiquement une définition, car le compilateur connaît la quantité d’espace à allouer.

L’exemple suivant montre des déclarations qui sont également des définitions :

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
    Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

Voici quelques déclarations qui ne sont pas des définitions :

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Typedefs et instructions using

Dans les versions antérieures C++de, le mot clé [typedef](aliases-and-typedefs-cpp.md) est utilisé pour déclarer un nouveau nom qui est un *alias* pour un autre nom. Par exemple, le type `std::string` est un autre nom pour `std::basic_string<char>`. Il doit être évident que les programmeurs utilisent le nom typedef et non le nom réel. Dans moderne C++, le mot clé [using](aliases-and-typedefs-cpp.md) est préféré par rapport à typedef, mais l’idée est la même : un nouveau nom est déclaré pour une entité qui est déjà déclarée et définie.

## <a name="static-class-members"></a>Membres de classe statique

Étant donné que les membres de données de classe statique sont des variables discrètes partagées par tous les objets de la classe, ils doivent être définis et initialisés en dehors de la définition de classe. (Pour plus d’informations, consultez [classes](../cpp/classes-and-structs-cpp.md).)

## <a name="extern-declarations"></a>déclarations extern

Un C++ programme peut contenir plusieurs unités de [compilation](header-files-cpp.md). Pour déclarer une entité qui est définie dans une unité de compilation distincte, utilisez le mot clé [extern](extern-cpp.md) . Les informations contenues dans la déclaration sont suffisantes pour le compilateur, mais si la définition de l’entité est introuvable dans l’étape de liaison, l’éditeur de liens génère une erreur.

## <a name="in-this-section"></a>Contenu de cette section

[Classes de stockage](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[Initialiseurs](initializers.md)<br/>
[Alias et typedefs](aliases-and-typedefs-cpp.md)<br/>
[déclaration using](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[Attributs dansC++](attributes.md)<br/>

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)<br/>
