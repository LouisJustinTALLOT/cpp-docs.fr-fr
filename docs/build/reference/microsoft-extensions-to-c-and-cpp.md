---
title: Extensions Microsoft pour C et C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 903ad9d5a44bb455bede52aa3456d03456f54d13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379339"
---
# <a name="microsoft-extensions-to-c-and-c"></a>Extensions Microsoft pour C et C++
Visual C++ étend les normes ANSI C et ANSI C++ comme suit.  
  
## <a name="keywords"></a>Mots clés  
 Plusieurs mots clés sont ajoutés. Dans la liste [mots clés](../../cpp/keywords-cpp.md), les mots clés qui ont deux traits de soulignement de début sont des extensions de Visual C++.  
  
## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>En dehors des membres de la définition de classe static, const, Integral (ou enum)  
 Sous le standard (**/Za**), vous devez apporter une définition hors classe pour les membres de données, comme indiqué ici :  
  
```  
  
      class CMyClass  {  
   static const int max = 5;  
   int m_array[max];  
}  
...  
const int CMyClass::max;   // out of class definition  
```  
  
 Sous **/Ze**, la définition hors classe est facultative pour les membres de données static, const integral et const enum. Seuls les membres integral et enum qui sont de type static et const peuvent avoir des initialiseurs dans une classe ; l'expression d'initialisation doit être une expression de type const.  
  
 Pour éviter des erreurs quand une définition hors classe est fournie dans un en-tête de fichier et le fichier d’en-tête est inclus dans plusieurs fichiers sources, utilisez [selectany](../../cpp/selectany.md). Par exemple :  
  
```  
__declspec(selectany) const int CMyClass::max = 5;  
```  
  
## <a name="casts"></a>Casts  
 Le compilateur C++ et le compilateur C prennent tous les deux en charge les types de casts non ANSI suivants :  
  
-   Casts non ANSI pour produire des valeurs l-value. Par exemple :  
  
    ```  
    char *p;  
    (( int * ) p )++;  
    ```  
  
    > [!NOTE]
    >  Cette extension est disponible uniquement dans le langage C. Vous pouvez utiliser le format ANSI C suivant dans le code C++ pour modifier un pointeur comme s'il s'agit d'un pointeur vers un autre type.  
  
     L'exemple précédent peut être réécrit comme suit pour être conforme à la norme ANSI C.  
  
    ```  
    p = ( char * )(( int * )p + 1 );  
    ```  
  
-   Casts non ANSI d'un pointeur de fonction vers un pointeur de données. Par exemple :  
  
    ```  
    int ( * pfunc ) ();   
    int *pdata;  
    pdata = ( int * ) pfunc;  
    ```  
  
     Pour effectuer le même cast tout en conservant la compatibilité ANSI, vous pouvez effectuer un cast du pointeur de fonction vers `uintptr_t` avant d'effectuer un cast de celui-ci vers un pointeur de données :  
  
    ```  
    pdata = ( int * ) (uintptr_t) pfunc;  
    ```  
  
## <a name="variable-length-argument-lists"></a>Listes d’arguments de longueur variable  
 Le compilateur C et le compilateur C++ prennent les tous deux en charge un déclarateur de fonction qui spécifie un nombre variable d’arguments, suivi d’une définition de fonction qui fournit un type à la place :  
  
```  
void myfunc( int x, ... );  
void myfunc( int x, char * c )  
{ }  
```  
  
## <a name="single-line-comments"></a>Commentaires sur une ligne  
 Le compilateur C prend en charge les commentaires sur une seule ligne, qui commencent par deux barres obliques (//) :  
  
```  
// This is a single-line comment.  
```  
  
## <a name="scope"></a>Portée  
 Le compilateur C prend en charge les fonctionnalités suivantes liées à la portée.  
  
-   Redéfinitions des éléments extern comme static :  
  
    ```  
    extern int clip();  
    static int clip()  
    {}  
    ```  
  
-   Utilisation de redéfinitions typedef bénignes dans la même portée :  
  
    ```  
    typedef int INT;  
    typedef int INT;  
    ```  
  
-   Déclarateurs de fonction ont une portée de fichier :  
  
    ```  
    void func1()  
    {  
        extern int func2( double );  
    }  
    int main( void )  
    {  
        func2( 4 );    //  /Ze passes 4 as type double  
    }                  //  /Za passes 4 as type int  
    ```  
  
-   Utilisation de variables de portée de bloc qui sont initialisées à l'aide d'expressions non constantes :  
  
    ```  
    int clip( int );  
    int bar( int );  
    int main( void )  
    {  
        int array[2] = { clip( 2 ), bar( 4 ) };  
    }  
    int clip( int x )  
    {  
        return x;  
    }  
    int bar( int x )  
    {  
        return x;  
    }  
    ```  
  
## <a name="data-declarations-and-definitions"></a>Définitions et déclarations de données  
 Le compilateur C prend en charge les fonctionnalités de définition et de déclaration de données suivantes.  
  
-   Constantes de caractère et de chaîne mixtes dans un initialiseur :  
  
    ```  
    char arr[5] = {'a', 'b', "cde"};  
    ```  
  
-   Les champs qui ont des types de base autres que de bits **int non signées** ou **type signed int**.  
  
-   Déclarateurs qui n'ont pas de type :  
  
    ```  
    x;  
    int main( void )  
    {  
        x = 1;  
    }  
    ```  
  
-   Tableaux non dimensionnés comme dernier champ dans les structures et unions :  
  
    ```  
    struct zero  
    {  
        char *c;  
        int zarray[];  
    };  
    ```  
  
-   Structures sans nom (anonymes) :  
  
    ```  
    struct  
    {  
        int i;  
        char *s;  
    };  
    ```  
  
-   Unions sans nom (anonymes) :  
  
    ```  
    union  
    {  
        int i;  
        float fl;  
    };  
    ```  
  
-   Membres sans nom :  
  
    ```  
    struct s  
    {  
       unsigned int flag : 1;  
       unsigned int : 31;  
    }  
    ```  
  
## <a name="intrinsic-floating-point-functions"></a>Fonctions en virgule flottante intrinsèques  
 Le compilateur C++ et le compilateur C prend en charge la génération inline **x86 spécifique >** de la `atan`, `atan2`, `cos`, `exp`, `log`, `log10`, `sin`, `sqrt`, et `tan` fonctions **fin x86 spécifique** lorsque **/Oi** est spécifié. Pour le compilateur C, la conformité ANSI n'est plus assurée quand ces fonctions intrinsèques sont utilisées, car elles ne définissent pas la variable `errno`.  
  
## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Passage d’un paramètre de pointeur Non Const à une fonction qui attend une référence à un paramètre de pointeur Const  
 Il s’agit d’une extension C++. Ce code est compilé avec **/Ze**:  
  
```  
typedef   int   T;  
  
const T  acT = 9;      // A constant of type 'T'  
const T* pcT = &acT;   // A pointer to a constant of type 'T'  
  
void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'  
{  
   rpcT = pcT;  
}  
  
T*   pT;               // A pointer to a 'T'  
  
void func ()  
{  
   func2 ( pT );      // Should be an error, but isn't detected  
   *pT   = 7;         // Invalidly overwrites the constant 'acT'  
}  
```  
  
## <a name="iso646h-not-enabled"></a>ISO646. H ne pas activé  
 Sous **/Ze**, vous devez inclure iso646.h si vous souhaitez utiliser les formulaires de texte des opérateurs suivants :  
  
-   && (and)  
  
-   &= (and_eq)  
  
-   & (bitand)  
  
-   &#124;(bitor)  
  
-   ~ (Terminer)  
  
-   ! (not)  
  
-   ! = (not_eq)  
  
-   &#124;&#124;(ou)  
  
-   &#124;= (or_eq)  
  
-   ^ (xor)  
  
-   ^ = (xor_eq)  
  
## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>L'adresse du littéral de chaîne est de type const char [], et non const char (*) []  
 L’exemple suivant produira char const (\*) [4] sous **/Za**, mais char const [4] sous **/Ze**.  
  
```  
#include <stdio.h>  
#include <typeinfo>  
  
int main()  
{  
    printf_s("%s\n", typeid(&"abc").name());  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [/ Za, /Ze (désactiver les Extensions de langage)](../../build/reference/za-ze-disable-language-extensions.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)