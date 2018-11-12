---
title: '#ligne de la Directive (C/C++)'
ms.date: 10/18/2017
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: e478d287af097081910d192e2ac0fbee6890bfa2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614758"
---
# <a name="line-directive-cc"></a>#line, directive (C/C++)

Le **#line** directive indique au préprocesseur de modifier le numéro de ligne stocké en interne du compilateur et nom de fichier à un numéro de ligne donné et un nom de fichier.

## <a name="syntax"></a>Syntaxe

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>Notes

Le compilateur utilise le numéro de ligne et le nom de fichier facultatif pour faire référence à des erreurs qu’il trouve pendant la compilation. Le numéro de ligne fait généralement référence à la ligne d’entrée actuelle, et le nom de fichier fait référence au fichier d’entrée actuel. Le numéro de ligne est incrémenté une fois que chaque ligne est traitée.

Le *séquence de chiffres* valeur peut être une constante entière. Remplacement de macro peut être effectuée sur les jetons de prétraitement, mais le résultat doit correspondre à la syntaxe correcte. Le *filename* peut être n’importe quelle combinaison de caractères et doit être placée entre guillemets doubles (**» «**). Si *filename* est omis, le nom de fichier précédent reste inchangé.

Vous pouvez modifier le numéro de ligne source et le nom de fichier en écrivant un **#line** directive. Le traducteur utilise le numéro de ligne et le nom de fichier pour déterminer les valeurs des macros prédéfinies `__FILE__` et `__LINE__`. Vous pouvez utiliser ces macros à insérer des messages d’erreur autodescriptives dans le texte du programme. Pour plus d’informations sur ces macros prédéfinies, consultez [Macros prédéfinies](../preprocessor/predefined-macros.md).

Le `__FILE__` macro se développe en une chaîne dont le contenu est le nom de fichier, entouré de guillemets doubles (**» «**).

Si vous modifiez le numéro de ligne et le nom de fichier, le compilateur ignore les valeurs précédentes et continue le traitement avec les nouvelles valeurs. Le **#line** directive est généralement utilisée par les générateurs de programme pour générer des messages d’erreur faire référence au fichier source d’origine au lieu d’au programme généré.

Les exemples suivants illustrent **#line** et `__LINE__` et `__FILE__` macros.

Dans cette instruction, le numéro de ligne stocké en interne est défini sur 151 et le nom de fichier est modifié en copy.c.

```cpp
#line 151 "copy.c"
```

Dans cet exemple, la macro `ASSERT` utilise les macros prédéfinies `__LINE__` et `__FILE__` pour imprimer un message d’erreur sur le fichier source si une assertion donnée n’est pas remplie.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)