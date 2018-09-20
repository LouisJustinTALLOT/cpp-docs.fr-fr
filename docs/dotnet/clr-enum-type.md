---
title: Type Enum du CLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scope, of CLR enum
- enum struct keyword [C++]
- enum class keyword [C++]
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a39c451bcff7b5b3b1d7dd9f0d3925616b9d6aab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436222"
---
# <a name="clr-enum-type"></a>Type Enum du CLR

La déclaration et le comportement des enums a changé entre les Extensions managées pour C++ vers Visual C++.

La déclaration d’enum Extensions managées est précédée par le `__value` mot clé. L’idée ici est de distinguer l’enum natif de l’enum du CLR qui est dérivée de `System::ValueType`, tout en suggérant des fonctionnalités analogues. Exemple :

```
__value enum e1 { fail, pass };
public __value enum e2 : unsigned short  {
   not_ok = 1024,
   maybe, ok = 2048
};
```

La nouvelle syntaxe résout le problème de faire la distinction natif et les enums CLR en mettant l’accent sur la nature de la classe de ce dernier plutôt que ses racines de type valeur. Par conséquent, le `__value` mot clé est ignoré et remplacé par la paire de mots clés espacés de `enum class`. Cela fournit une symétrie de paires de mots clés pour les déclarations de référence, valeur, les classes d’interface :

```
enum class ec;
value class vc;
ref class rc;
interface class ic;
```

La traduction de la paire d’énumération `e1` et `e2` dans la nouvelle syntaxe se présente comme suit :

```
enum class e1 { fail, pass };
public enum class e2 : unsigned short {
   not_ok = 1024,
   maybe, ok = 2048
};
```

Mis à part ce petit changement syntaxique, le comportement du type enum CLR a été modifié dans une de plusieurs façons :

- Une déclaration anticipée d’un enum du CLR n’est plus pris en charge. Il n’existe aucun mappage. Elle est simplement signalée comme une erreur de compilation.

```
__value enum status; // Managed Extensions: ok
enum class status;   // new syntax: error
```

- La résolution de surcharge entre les types arithmétiques intégrés et la `Object` hiérarchie de classes a été inversée entre les deux versions du langage ! Comme un effet secondaire, les enums CLR sont ne sont plus converties implicitement en types arithmétiques.

- Dans la nouvelle syntaxe, un enum du CLR conserve sa propre portée, ce qui n’est pas le cas dans les Extensions managées. Auparavant, les énumérateurs étaient visibles dans la portée contenant l’enum. Maintenant, les énumérateurs sont encapsulés dans la portée de l’enum.

## <a name="clr-enums-are-a-kind-of-object"></a>Les Enums CLR sont une sorte d’objet

Prenons le fragment de code suivant :

```
__value enum status { fail, pass };

void f( Object* ){ Console::WriteLine("f(Object)\n"); }
void f( int ){ Console::WriteLine("f(int)\n"); }

int main()
{
   status rslt = fail;

   f( rslt ); // which f is invoked?
}
```

Pour le programmeur en C++ natif, naturel de réponses à la question quelle instance surchargée `f()` est appelée est celle de `f(int)`. Un enum est une constante intégrale symbolique et il participe dans les promotions intégrales standards qui sont prioritaires dans ce cas.  Et en fait dans les Extensions managées, c’était l’instance à laquelle l’appel résout. Cela a provoqué un nombre de surprises - pas lorsque nous avons utilisé dans un état d’esprit C++ natif - mais lorsque nous avions besoin qu’ils interagissent avec l’infrastructure existante de la BCL (bibliothèque de classes de Base), où un `Enum` est une classe dérivée indirectement de `Object`. Dans la conception du langage Visual C++, l’instance de `f()` appelée est celle de `f(Object^)`.

Le que Visual C++ a choisi d’appliquer cette recommandation consiste à ne prend ne pas en charge les conversions implicites entre un type enum du CLR et les types arithmétiques. Cela signifie qu’une affectation d’un objet d’un type enum du CLR à un type arithmétique nécessite un cast explicite. Ainsi, par exemple, étant donné

```
void f( int );
```

comme une méthode non surchargée, dans les Extensions managées, l’appel

```
f( rslt ); // ok: Managed Extensions; error: new syntax
```

est OK et la valeur contenue dans `rslt` est converti implicitement en une valeur entière. Dans Visual C++, cet appel ne parvient pas à compiler. Pour traduire correctement, nous devons insérer un opérateur de conversion :

```
f( safe_cast<int>( rslt )); // ok: new syntax
```

## <a name="the-scope-of-the-clr-enum-type"></a>L’étendue du Type Enum CLR

Une des modifications entre les langages C et C++ a été l’ajout en C++ de la portée au sein de l’installation de struct. En C, un struct est simplement un agrégat de données sans prise en charge d’une interface ou d’une portée associée. Cela a été un changement radical en temps et a été un sujet de controverse pour de nombreux utilisateurs C++ nouvelle provenant du langage C. La relation entre le natif et un enum du CLR est analogue.

Dans les Extensions managées, une tentative a été effectuée pour définir des noms injectés faiblement pour les énumérateurs d’un enum du CLR afin de simuler l’absence de portée dans une énumération native. Cela n’a pas abouti. Le problème est que cela entraîne les énumérateurs pour dispersés dans l’espace de noms global, ce qui entraîne difficile à gérer les conflits de noms. Dans la nouvelle syntaxe, nous nous sommes conformés aux autres langages CLR prise en charge des portées au sein de l’enum du CLR.

Cela signifie que toute utilisation non qualifiée d’un énumérateur d’un enum du CLR n’est pas reconnue par la nouvelle syntaxe. Examinons un exemple concret.

```
// Managed Extensions supporting weak injection
__gc class XDCMake {
public:
   __value enum _recognizerEnum {
      UNDEFINED,
      OPTION_USAGE,
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,
      XDC0002_ERR_CANNOT_WRITE_TO = 2,
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,
      XDC0004_WRN_XML_LOAD_FAILURE = 4,
      XDC0006_WRN_NONEXISTENT_FILES = 6,
   };

   ListDictionary* optionList;
   ListDictionary* itagList;

   XDCMake() {
      optionList = new ListDictionary;

      // here are the problems...
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)

      itagList = new ListDictionary;
      itagList->Add(S"returns",
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)
   }
};
```

Chacun des trois non qualifiés utilise des noms d’énumérateur (`(1)`, `(2)`, et `(3)`) devra être qualifié dans la traduction vers la nouvelle syntaxe afin que le code source à compiler. Voici une traduction correcte du code source d’origine :

```
ref class XDCMake {
public:
   enum class _recognizerEnum {
      UNDEFINED, OPTION_USAGE,
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,
      XDC0002_ERR_CANNOT_WRITE_TO = 2,
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,
      XDC0004_WRN_XML_LOAD_FAILURE = 4,
      XDC0006_WRN_NONEXISTENT_FILES = 6
   };

   ListDictionary^ optionList;
   ListDictionary^ itagList;

   XDCMake() {
      optionList = gcnew ListDictionary;
      optionList->Add("?",_recognizerEnum::OPTION_USAGE); // (1)
      optionList->Add("help",_recognizerEnum::OPTION_USAGE); //(2)
      itagList = gcnew ListDictionary;
      itagList->Add( "returns",
         _recognizerEnum::XDC0004_WRN_XML_LOAD_FAILURE); //(3)
   }
};
```

Cela modifie la stratégie de conception entre natif et un enum du CLR. Avec un enum du CLR conservant une portée associée dans Visual C++, il n’est ni nécessaire ni efficace d’encapsuler la déclaration de l’enum dans une classe. Cet idiome a évolué à l’époque de cfront 2.0 dans les laboratoires Bell également afin de résoudre le problème de la pollution de nom global.

Dans la version bêta d’origine de la nouvelle bibliothèque iostream par Jerry Schwarz dans les laboratoires Bell, Jerry n’avait pas encapsulé tous les enums associés définis pour la bibliothèque et les énumérateurs courants tels que `read`, `write`, `append`, et ainsi de suite , effectués presque impossible pour les utilisateurs à se compiler leur code existant. Une solution aurait été de supprimer les noms, tel que `io_read`, `io_write`, etc. Une autre solution aurait été de modifier le langage en ajoutant la portée à un enum, mais cela n’était pas possible en temps. La solution intermédiaire a été pour encapsuler l’enum dans la classe ou la hiérarchie de classes, où le nom de balise et les énumérateurs de l’enum remplissent la portée de classe englobante.) Autrement dit, la motivation pour placer des enums dans des classes, au moins à l’origine, n’était pas théorique, mais une réponse pratique au problème pollution d’espace de noms global.

Avec l’enum Visual C++, il n’est plus avantage majeur pour encapsuler un enum dans une classe. En fait, si vous examinez le `System` espaces de noms, vous verrez qu’enums, classes et interfaces habitent tous le même espace de déclaration.

## <a name="see-also"></a>Voir aussi

[Types valeur et leurs comportements (C++-CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[enum, classe](../windows/enum-class-cpp-component-extensions.md)