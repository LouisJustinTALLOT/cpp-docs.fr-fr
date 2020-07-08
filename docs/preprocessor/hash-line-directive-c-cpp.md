---
title: '#line, directive (C/C++)'
description: 'Décrit la directive #line, utilisée pour définir le numéro de ligne et le nom de fichier signalés par les macros de préprocesseur.'
ms.date: 07/06/2020
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 7b671cfdf5d5ce43024ac3e038c214396ac8679c
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058618"
---
# <a name="line-directive-cc"></a>#line, directive (C/C++)

La directive **#line** indique au préprocesseur de définir les valeurs signalées du compilateur pour le numéro de ligne et le nom de fichier sur un numéro de ligne et un nom de fichier donnés.

## <a name="syntax"></a>Syntax

> **`#line`***digit-Sequence* ["*nom_fichier*"]

## <a name="remarks"></a>Remarques

Le compilateur utilise le numéro de ligne et le nom de fichier facultatif pour faire référence aux erreurs qu’il trouve pendant la compilation. Le numéro de ligne fait généralement référence à la ligne d’entrée en cours et le nom de fichier fait référence au fichier d’entrée en cours. Le numéro de ligne est incrémenté après le traitement de chaque ligne.

La valeur *de la séquence digit* peut être n’importe quelle constante entière. Le remplacement de macro peut être utilisé sur les jetons de prétraitement, mais le résultat doit correspondre à la syntaxe correcte. Le *nom de fichier* peut être n’importe quelle combinaison de caractères et doit être placé entre guillemets doubles ( `" "` ). Si *filename* est omis, le nom de fichier précédent reste inchangé.

Vous pouvez modifier le numéro de ligne source et le nom de fichier en écrivant une **`#line`** directive. La **`#line`** directive définit la valeur de la ligne qui suit immédiatement la directive dans le fichier source. Le traducteur utilise le numéro de ligne et le nom de fichier pour déterminer les valeurs des macros prédéfinies `__FILE__` et `__LINE__` . Vous pouvez utiliser ces macros pour insérer des messages d’erreur auto-descriptifs dans le texte du programme. Pour plus d’informations sur ces macros prédéfinies, consultez [macros prédéfinies](../preprocessor/predefined-macros.md).

La `__FILE__` macro se développe en une chaîne dont le contenu est le nom de fichier, entouré par des guillemets doubles ( `" "` ).

Si vous modifiez le numéro de ligne et le nom de fichier, le compilateur ignore les valeurs précédentes et continue le traitement avec les nouvelles valeurs. La directive **#line** est généralement utilisée par les générateurs de programmes. Elle est utilisée pour faire en sorte que les messages d’erreur fassent référence au fichier source d’origine, et non au programme généré.

## <a name="example"></a>Exemple

Les exemples suivants illustrent **`#line`** les `__LINE__` `__FILE__` macros et.

Dans le premier exemple, le numéro de ligne est défini sur 10, puis sur 20 et le nom de fichier est remplacé par *Hello. cpp*.

```cpp
// line_directive.cpp
// Compile by using: cl /W4 /EHsc line_directive.cpp
#include <stdio.h>

int main()
{
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 10
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 20 "hello.cpp"
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
}
```

```Output
This code is on line 7, in file line_directive.cpp
This code is on line 10, in file line_directive.cpp
This code is on line 20, in file hello.cpp
This code is on line 21, in file hello.cpp
```

Dans cet exemple, la macro `ASSERT` utilise les macros prédéfinies `__LINE__` et `__FILE__` affiche un message d’erreur relatif au fichier source si une assertion donnée n’est pas vérifiée.

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
