---
title: Navigation dans le système de fichiers
ms.date: 11/04/2016
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: f5fe8d29baae76b1e7fb851bf04f4c6b32215a8e
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076540"
---
# <a name="file-system-navigation"></a>Navigation dans le système de fichiers

L’en-tête \<filesystem> implémente la spécification technique de système de fichiers C++ (C++ File System Technical Specification) ISO/IEC TS 18822:2015 (Projet final : [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)), et a des types et des fonctions qui vous permettent d’écrire du code indépendant des plateformes pour naviguer dans le système de fichiers. Comme il est interplateforme, il contient des API qui ne s'appliquent pas aux systèmes Windows. Par exemple, cela signifie que `is_fifo(const path&)` retourne toujours la **valeur false** sur Windows.

## <a name="overview"></a>Vue d’ensemble

Utilisez les API \<filesystem> pour les tâches suivantes :

- effectuer une itération des fichiers et répertoires sous un chemin d'accès spécifié ;

- obtenir des informations sur les fichiers (date de création, taille, extension, répertoire racine, etc.) ;

- composer, décomposer et comparer des chemins d'accès ;

- créer, copier et supprimer des répertoires ;

- copier et supprimer des fichiers.

Pour plus d’informations sur les E/S de fichiers avec la bibliothèque standard, consultez [iostream, programmation](../standard-library/iostream-programming.md).

## <a name="paths"></a>Chemins

### <a name="constructing-and-composing-paths"></a>Construction et composition de chemins d'accès

Dans Windows (depuis XP), les chemins d'accès sont stockés en mode natif au format Unicode. La classe [path](../standard-library/path-class.md) effectue automatiquement toutes les conversions de chaînes nécessaires. Elle accepte les arguments des tableaux de caractères larges et étroits, ainsi que des types `std::string` et `std::wstring` au format UTF8 ou UTF16. La classe `path` normalise aussi automatiquement les séparateurs des chemins. Vous pouvez utiliser une seule barre oblique comme séparateur de répertoires dans les arguments de constructeur. Cela vous permet d'utiliser les mêmes chaînes pour stocker des chemins d'accès dans les environnements Windows et UNIX :

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Pour concaténer deux chemins, utilisez les opérateurs `/` et `/=` surchargés, qui sont similaires aux opérateurs `+` et `+=` sur `std::string` et `std::wstring`. Si ce n’est pas le cas, l’objet `path` fournira facilement les séparateurs.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Examen des chemins d'accès

La classe path contient plusieurs méthodes qui retournent des informations sur différents éléments du chemin d'accès proprement dit, de manière distincte de l'entité système de fichiers à laquelle il fait référence. Vous pouvez ainsi obtenir la racine, le chemin d'accès relatif, le nom et l'extension de fichier, etc. Vous pouvez itérer un objet path pour examiner tous les répertoires de l'arborescence. L'exemple suivant montre comment itérer un chemin d'accès (pas le répertoire qu'il référence) et récupérer des informations sur les éléments qui le composent.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main(int argc, char* argv[])
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Le code génère cette sortie :

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>Comparaison des chemins d'accès

La classe `path` surcharge les mêmes opérateurs de comparaison que `std::string` et `std::wstring`. Quand vous comparez deux chemins d'accès, vous effectuez une comparaison de chaînes une fois que les séparateurs ont été normalisés. Si une barre oblique de fin (ou barre oblique inverse) est manquante, elle n'est pas ajoutée, ce qui a une incidence sur la comparaison. L'exemple suivant montre comment les valeurs de chemin d'accès sont comparées :

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

Pour exécuter ce code, collez-le dans l’exemple complet ci-dessus avant `main` et supprimez les commentaires de la ligne qui l’appelle dans la fonction main.

### <a name="converting-between-path-and-string-types"></a>Conversion entre les types chemin d'accès et chaîne

Un objet `path` est implicitement convertible en `std::wstring` ou en `std::string`. Cela signifie que vous pouvez passer un chemin à des fonctions comme [wofstream::open](../standard-library/basic-ofstream-class.md#open), comme illustré dans cet exemple :

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

int main(int argc, char* argv[])
{
    wchar_t* p = L"C:/Users/Public/Documents";
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>Itération de répertoires et de fichiers

L’en-tête \<filesystem> fournit le type [directory_iterator](../standard-library/directory-iterator-class.md) pour itérer sur des répertoires uniques, et la classe [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pour itérer de manière récursive sur un répertoire et tous ses sous-répertoires. Après avoir construit un itérateur en lui passant un objet `path` , l’itérateur pointe vers le premier objet directory_entry dans le chemin. Créez l'itérateur de fin en appelant le constructeur par défaut.

Lors d'une itération d'un répertoire, plusieurs types d'éléments peuvent être examinés, tels que des répertoires, des fichiers, des liens symboliques et des fichiers socket, entre autres. `directory_iterator` retourne ses éléments sous la forme d’objets [directory_entry](../standard-library/directory-entry-class.md).
