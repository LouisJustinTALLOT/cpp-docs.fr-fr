---
title: static_assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_assert_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc51fab2dade4c6bed0456dd353258df82722de5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943836"
---
# <a name="staticassert"></a>static_assert
Teste une assertion logicielle au moment de la compilation. Si l’expression de constante spécifiée a la valeur FALSE, le compilateur affiche le message spécifié, si un est fourni, et la compilation échoue avec l’erreur C2338 ; Sinon, la déclaration n’a aucun effet.  
  
## <a name="syntax"></a>Syntaxe  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`constant-expression`|Expression constante intégrale pouvant être convertie en expression booléenne.<br /><br /> Si l'expression évaluée a la valeur zéro (fausse), le paramètre `string-literal` s'affiche et la compilation échoue avec une erreur. Si l’expression est différente de zéro (true), le **static_assert** déclaration n’a aucun effet.|  
|`string-literal`|Message qui s'affiche si le paramètre `constant-expression` a la valeur zéro. Le message est une chaîne de caractères dans le [jeu de caractères de base](../c-language/ascii-character-set.md) du compilateur ; c'est-à-dire, pas [caractères multioctets ou larges](../c-language/multibyte-and-wide-characters.md).|  
  
## <a name="remarks"></a>Notes  
 Le `constant-expression` paramètre d’un **static_assert** déclaration représente un *assertion logicielle*. Une assertion logicielle spécifie une condition supposée être vraie en un point particulier de votre programme. Si la condition est true, le **static_assert** déclaration n’a aucun effet. Si la condition est fausse, l'assertion échoue, le compilateur affiche le message dans le paramètre `string-literal` et la compilation échoue avec une erreur. Dans Visual Studio 2017 et versions ultérieures, le paramètre de littéral de chaîne est facultatif. 
  
 Le **static_assert** déclaration teste une assertion logicielle au moment de la compilation. En revanche, le [assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro teste une assertion logicielle au moment de l’exécution et génère un coût d’exécution dans l’espace ou de temps. Le **static_assert** déclaration est particulièrement utile pour déboguer des modèles, car les arguments template peuvent être inclus dans le `constant-expression` paramètre.  
  
 Le compilateur examine la **static_assert** déclaration pour les erreurs de syntaxe lors de la déclaration est rencontrée. Le compilateur évalue immédiatement le paramètre `constant-expression` s'il ne dépend pas d'un paramètre de modèle. Sinon, le compilateur évalue le paramètre `constant-expression` lorsque le modèle est instancié. Par conséquent, le compilateur peut publier un message de diagnostic une fois la déclaration rencontrée, puis à nouveau lorsque le modèle est instancié.  
  
 Vous pouvez utiliser la **static_assert** mot clé à l’espace de noms, classe ou portée de bloc. (Le **static_assert** mot clé est techniquement une déclaration, même s’il n’introduit pas de nouveau nom dans votre programme, car il peut être utilisé à la portée de l’espace de noms.)  
  
## <a name="description"></a>Description  
 Dans l’exemple suivant, le **static_assert** déclaration a une portée de l’espace de noms. Comme le compilateur connaît la taille du type `void *`, l'expression est évaluée immédiatement.  
  
## <a name="example"></a>Exemple  
  
```cpp 
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>Description  
 Dans l’exemple suivant, le **static_assert** déclaration a une portée de classe. Le **static_assert** vérifie qu’un paramètre de modèle est un *données* type (POD). Le compilateur examine la **static_assert** déclaration lorsqu’elle est déclarée, mais n’évalue pas le `constant-expression` paramètre jusqu'à ce que le `basic_string` modèle de classe est instancié dans `main()`.  
  
## <a name="example"></a>Exemple  
  
```cpp 
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(std::is_pod<CharT>::value,  
                  "Template argument CharT must be a POD type in class template basic_string");  
    // ...  
    };  
}  
  
struct NonPOD {  
    NonPOD(const NonPOD &) {}  
    virtual ~NonPOD() {}  
};  
  
int main()  
{  
    std::basic_string<char> bs;  
}  
```  
  
## <a name="description"></a>Description  
 Dans l’exemple suivant, le **static_assert** déclaration a une portée de bloc. Le **static_assert** vérifie que la taille de la structure VMPage est égale à la valeur de pagesize de mémoire virtuelle du système.  
  
## <a name="example"></a>Exemple  
  
```cpp 
#include <sys/param.h> // defines PAGESIZE  
class VMMClient {  
public:  
    struct VMPage { // ...   
           };  
    int check_pagesize() {  
    static_assert(sizeof(VMPage) == PAGESIZE,  
        "Struct VMPage must be the same size as a system virtual memory page.");  
    // ...  
    }  
// ...  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Assertion et Messages fournis par l’utilisateur (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [#error (directive) (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [Macro assert, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [Modèles](../cpp/templates-cpp.md)   
 [Jeu de caractères ASCII](../c-language/ascii-character-set.md)   
 [Déclarations et définitions](declarations-and-definitions-cpp.md)