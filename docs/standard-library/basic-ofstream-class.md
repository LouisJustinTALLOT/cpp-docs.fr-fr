---
title: basic_ofstream, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
dev_langs: C++
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 235bf7fc118f8752adefc61f5ed18ea01caec727
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="basicofstream-class"></a>basic_ofstream, classe
Décrit un objet qui contrôle l’insertion d’éléments et d’objets codés dans une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> avec des éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ofstream : public basic_ostream<Elem, Tr>
```  
  
#### <a name="parameters"></a>Paramètres  
 `Elem`  
 Élément de base de la mémoire tampon de fichier.  
  
 `Tr`  
 Caractéristiques de l’élément de base de la mémoire tampon de fichier (généralement `char_traits`< `Elem`>).  
  
## <a name="remarks"></a>Notes  
 Quand la spécialisation `wchar_t` de `basic_ofstream` écrit dans le fichier, si celui-ci est ouvert en mode texte, elle écrit une séquence MBCS. La représentation interne utilisera une mémoire tampon de caractères `wchar_t`.  
  
 L’objet stocke un objet de classe `basic_filebuf`< `Elem`, `Tr`>.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer un objet `basic_ofstream` et y écrire du texte.  
  
```  
// basic_ofstream_class.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
### <a name="constructors"></a>Constructeurs  
  
|||  
|-|-|  
|[basic_ofstream](#basic_ofstream)|Crée un objet de type `basic_ofstream`.|  
  
### <a name="member-functions"></a>Fonctions membres  
  
|||  
|-|-|  
|[close](#close)|Ferme un fichier.|  
|[is_open](#is_open)|Détermine si un fichier est ouvert.|  
|[open](#open)|Ouvre un fichier.|  
|[rdbuf](#rdbuf)|Retourne l'adresse de la mémoire tampon de flux stockée.|  
|[swap](#swap)|Échange le contenu de ce `basic_ofstream` avec le contenu du `basic_ofstream` fourni.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[operator=](#op_eq)|Assigne le contenu de cet objet de flux. Il s'agit d'une assignation de déplacement impliquant une `rvalue reference` qui ne laisse pas de copie.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<fstream>  
  
 **Espace de noms :** std  
  
##  <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream  
 Crée un objet de type `basic_ofstream`.  
  
```
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Filename`  
 Nom du fichier à ouvrir.  
  
 `_Mode`  
 Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Protection d’ouverture de fichier par défaut, équivalente au paramètre `shflag` dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
 `right`  
 Référence rvalue à l’objet `basic_ofstream` utilisé pour initialiser cet objet `basic_ofstream`.  
  
### <a name="remarks"></a>Notes  
 Le premier constructeur initialise la classe de base en appelant [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), où **sb** est l’objet stocké de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. Il initialise également **sb** en appelant `basic_filebuf`< `Elem`, `Tr`>.  
  
 Les deuxième et troisième constructeurs initialisent la classe de base en appelant `basic_ostream`( **sb**). Ils initialisent également **sb** en appelant `basic_filebuf`< `Elem`, `Tr`>, puis **sb**. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`). Si cette dernière fonction retourne un pointeur null, le constructeur appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
 Le quatrième constructeur est une fonction de copie. Il initialise l’objet avec le contenu de `right`, traité comme une référence rvalue.  
  
### <a name="example"></a>Exemple  
  L'exemple suivant montre comment créer un objet `basic_ofstream` et y écrire du texte.  
  
```  
// basic_ofstream_ctor.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("C:\\ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
##  <a name="close"></a>  basic_ofstream::close  
 Ferme un fichier.  
  
```
void close();
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre appelle [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[fermer](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Exemple  
  Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple qui utilise **close**.  
  
##  <a name="is_open"></a>  basic_ofstream::is_open  
 Indique si un fichier est ouvert.  
  
```
bool is_open() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si le fichier est ouvert, `false` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne [rdbuf](#rdbuf)  **->**  [is_open](../standard-library/basic-filebuf-class.md#is_open).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// basic_ofstream_is_open.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   ifstream file;  
   // Open and close with a basic_filebuf  
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );  
   file.close( );  
   if (file.is_open())  
      cout << "it's open" << endl;  
   else  
      cout << "it's closed" << endl;  
}  
```  
  
##  <a name="open"></a>  basic_ofstream::open  
 Ouvre un fichier.  
  
```
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Filename`  
 Nom du fichier à ouvrir.  
  
 `_Mode`  
 Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Protection d’ouverture de fichier par défaut, équivalente au paramètre `shflag` dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Notes  
 La fonction membre appelle [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out`). Si cette fonction retourne un pointeur null, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
### <a name="example"></a>Exemple  
  Consultez [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) pour obtenir un exemple qui utilise **open**.  
  
##  <a name="op_eq"></a>  basic_ofstream::operator=  
 Assigne le contenu de cet objet de flux. Il s'agit d'une assignation de déplacement impliquant une `rvalue reference` qui ne laisse pas de copie.  
  
```
basic_ofstream& operator=(basic_ofstream&& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `right`  
 Référence rvalue à un objet `basic_ofstream`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `*this`.  
  
### <a name="remarks"></a>Notes  
 L'opérateur membre remplace le contenu de l'objet à l'aide du contenu de `right`, traité comme une référence rvalue.  
  
##  <a name="rdbuf"></a>  basic_ofstream::rdbuf  
 Retourne l'adresse de la mémoire tampon de flux stockée.  
  
```
basic_filebuf<Elem, Tr> *rdbuf() const
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l'adresse de la mémoire tampon de flux stockée.  
  
### <a name="example"></a>Exemple  
  Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.  
  
##  <a name="swap"></a>  basic_ofstream::swap  
 Échange le contenu de deux objets `basic_ofstream`.  
  
```
void swap(basic_ofstream& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `right`  
 Référence `lvalue` à un autre objet `basic_ofstream`.  
  
### <a name="remarks"></a>Notes  
 La fonction membre échange le contenu de cet objet avec celui de `right`.  
  
## <a name="see-also"></a>Voir aussi  
 [basic_ostream, classe](../standard-library/basic-ostream-class.md)   
 [Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream, programmation](../standard-library/iostream-programming.md)   
 [iostreams, conventions](../standard-library/iostreams-conventions.md)



