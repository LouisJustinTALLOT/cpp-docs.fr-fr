---
title: Fonctions membres de flux de fichiers de sortie
ms.date: 11/04/2016
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
ms.openlocfilehash: 8c23008d0c46a532f11e89442328ed25cc203077
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453052"
---
# <a name="output-file-stream-member-functions"></a>Fonctions membres de flux de fichiers de sortie

Les fonctions membres de flux de sortie ont trois types : celles qui sont équivalentes aux manipulateurs, celles qui effectuent des opérations d'écriture non formatées et celles qui modifient autrement l'état du flux et n'ont aucun manipulateur ou opérateur d'insertion équivalent. Pour une sortie séquentielle mise en forme, vous ne pouvez utiliser que des opérateurs et manipulateurs d'insertion. Pour une sortie binaire sur disque à accès aléatoire, utilisez d'autres fonctions membres, avec ou sans opérateurs d'insertion.

## <a name="the-open-function-for-output-streams"></a>Fonction open pour les flux de sortie

Pour utiliser un flux de fichier de sortie ([ofstream](../standard-library/basic-ofstream-class.md)), vous devez associer ce flux à un fichier disque spécifique dans le constructeur `open` ou la fonction. Si vous utilisez la `open` fonction, vous pouvez réutiliser le même objet de flux avec une série de fichiers. Dans les deux cas, les arguments décrivant le fichier sont identiques.

Lorsque vous ouvrez le fichier associé à un flux de sortie, vous spécifiez `open_mode` généralement un indicateur. Vous pouvez combiner ces indicateurs, définis comme énumérateurs dans la classe `ios`, avec l’opérateur OR ( &#124; ) au niveau du bit. Consultez [ios_base::openmode](../standard-library/ios-base-class.md#openmode) pour obtenir la liste des énumérateurs.

Trois situations de flux de sortie courantes impliquent des options de mode :

- Création d'un fichier. Si le fichier existe déjà, l'ancienne version est supprimée.

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- Ajout d'enregistrements à un fichier existant ou création d'un fichier s'il n'existe pas.

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- Ouverture de deux fichiers, un par un, sur le même flux.

   ```cpp
   ofstream ofile();
   ofile.open("FILE1", ios::in);
   // Do some output
   ofile.close();    // FILE1 closed
   ofile.open("FILE2", ios::in);
   // Do some more output
   ofile.close();    // FILE2 closed
   // When ofile goes out of scope it is destroyed.
   ```

## <a name="the-put"></a>Le put

La fonction **put** écrit un caractère dans le flux de sortie. Les deux instructions suivantes sont identiques par défaut, mais la deuxième est affectée par les arguments de format du flux :

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>Écriture

La `write` fonction écrit un bloc de mémoire dans un flux de fichier de sortie. L’argument de longueur spécifie le nombre d’octets écrits. Cet exemple crée un flux de fichier de sortie et y écrit la valeur binaire de la structure `Date` :

```cpp
// write_function.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;

struct Date
{
   int mo, da, yr;
};

int main( )
{
   Date dt = { 6, 10, 92 };
   ofstream tfile( "date.dat" , ios::binary );
   tfile.write( (char *) &dt, sizeof dt );
}
```

La `write` fonction ne s’arrête pas lorsqu’elle atteint un caractère null, de sorte que la structure de la classe complète est écrite. La fonction accepte deux arguments: un pointeur de **type char** et un nombre de caractères à écrire. Notez le cast requis en **char** <strong>\*</strong> avant l’adresse de l’objet de structure.

## <a name="the-seekp-and-tellp-functions"></a>Fonctions seekp et tellp

Un flux de fichier de sortie conserve un pointeur interne qui pointe vers l'emplacement où les données doivent être écrites par la suite. La fonction membre `seekp` définit ce pointeur et fournit une sortie de fichier sur disque à accès aléatoire. La fonction membre `tellp` retourne l'emplacement du fichier. Pour obtenir des exemples qui utilisent les équivalents de flux d’entrée à `seekp` et `tellp`, consultez [Fonctions seekg et tellg](../standard-library/input-stream-member-functions.md).

## <a name="the-close-function-for-output-streams"></a>Fonction close pour les flux de sortie

La `close` fonction membre ferme le fichier de disque associé à un flux de fichier de sortie. Le fichier doit être fermé pour effectuer la sortie sur disque. Si nécessaire, le `ofstream` destructeur ferme le fichier pour vous, mais vous pouvez utiliser la `close` fonction si vous devez ouvrir un autre fichier pour le même objet de flux.

Le destructeur de flux de sortie ferme automatiquement le fichier d’un flux uniquement si le constructeur `open` ou la fonction membre a ouvert le fichier. Si vous transmettez au constructeur un descripteur de fichier pour un fichier déjà ouvert `attach` ou utilisez la fonction membre, vous devez fermer le fichier explicitement.

## <a name="vclrferrorprocessingfunctionsanchor10"></a> Fonctions de traitement des erreurs

Utilisez les fonctions membres ci-après pour tester les erreurs lors de l'écriture dans un flux :

|Fonction|Valeur de retour|
|--------------|------------------|
|[bad](basic-ios-class.md#bad)|Retourne **true** s’il se produit une erreur irrécupérable.|
|[fail](basic-ios-class.md#fail)|Retourne **true** s’il se produit une erreur irrécupérable ou une condition « attendue », par exemple une erreur de conversion, ou si le fichier est introuvable. Le traitement peut souvent reprendre après un appel `clear` à avec un argument égal à zéro.|
|[good](basic-ios-class.md#good)|Retourne **true** s’il n’y a pas de condition d’erreur (irrécupérable ou autre) et si l’indicateur de fin de fichier n’est pas défini.|
|[eof](basic-ios-class.md#eof)|Retourne **true** sur la condition de fin de fichier.|
|[clear](basic-ios-class.md#clear)|Définit l'état d'erreur interne. Si la fonction est appelée avec les arguments par défaut, elle efface tous les bits d’erreur.|
|[rdstate](basic-ios-class.md#rdstate|Retourne l'état d'erreur actuel.|

L’opérateur **!** l’opérateur est surchargé pour exécuter la même fonction que la `fail` fonction. Ainsi, l'expression :

```cpp
if(!cout)...
```

équivaut à :

```cpp
if(cout.fail())...
```

L’opérateur **void\*()** est surchargé pour être l’opposé de l’opérateur **!** . Ainsi, l’expression :

```cpp
if(cout)...
```

est égale à :

```cpp
if(!cout.fail())...
```

L' **opérateur\*void ()** n’est pas équivalent `good` à car il ne teste pas la fin du fichier.

## <a name="see-also"></a>Voir aussi

[Flux de sortie](../standard-library/output-streams.md)
