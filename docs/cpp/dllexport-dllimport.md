---
title: dllexport, dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: f03c945375cbe8c399e604e12f070b5a63d316f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221651"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Spécifique à Microsoft**

Les **`dllexport`** **`dllimport`** attributs de classe de stockage et sont des extensions spécifiques à Microsoft pour les langages C et C++. Vous pouvez les utiliser pour exporter et importer des fonctions, des données et des objets vers ou depuis une DLL.

## <a name="syntax"></a>Syntaxe

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Notes

Ces attributs définissent explicitement l'interface de la DLL à son client, qui peut être un fichier exécutable ou une autre DLL. Déclarer des fonctions comme **`dllexport`** élimine la nécessité d’un fichier de définition de module (. def), au moins en ce qui concerne la spécification des fonctions exportées. L' **`dllexport`** attribut remplace le mot clé **__export** .

Si une classe est marquée declspec(dllexport), les spécialisations des modèles de classe dans la hiérarchie de classes sont implicitement marquées comme declspec(dllexport). Cela signifie que les modèles de classe sont instanciés explicitement et que les membres de la classe doivent être définis.

**`dllexport`** d’une fonction expose la fonction avec son nom décoré. Pour les fonctions C++, cela inclut l'altération des noms. Pour les fonctions C ou les fonctions déclarées comme `extern "C"`, cela inclut la décoration propre à la plateforme basée sur la convention d’appel. Pour plus d’informations sur la décoration de noms dans le code C/C++, consultez [noms décorés](../build/reference/decorated-names.md). Aucune décoration de nom n’est appliquée aux fonctions C exportées ou aux `extern "C"` fonctions C++ à l’aide de la **`__cdecl`** Convention d’appel.

Pour exporter un nom non décoré, vous pouvez établir un lien à l'aide d'un fichier de définition de module (.def) qui définit le nom non décoré dans une section EXPORTS. Pour plus d’informations, consultez [exportations](../build/reference/exports.md). Une autre façon d’exporter un nom non décoré consiste à utiliser une `#pragma comment(linker, "/export:alias=decorated_name")` directive dans le code source.

Lorsque vous déclarez **`dllexport`** ou **`dllimport`** , vous devez utiliser la [syntaxe d’attribut étendu](../cpp/declspec.md) et le **`__declspec`** mot clé.

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

Pour plus d'informations, consultez les pages suivantes :

- [Définitions et déclarations](../cpp/definitions-and-declarations-cpp.md)

- [Définition de fonctions inline C++ avec dllexport et dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [Règles générales et limitations](../cpp/general-rules-and-limitations.md)

- [Utilisation de dllimport et dllexport dans les classes C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
