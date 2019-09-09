---
title: '#line, directive (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 35bee779ebf059c20d4a46e27b5ad4cbfb3ce5f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220224"
---
# <a name="line-directive-cc"></a>#line, directive (CC++/)

La directive **#line** indique au préprocesseur de modifier le numéro de ligne et le nom de fichier stockés en interne du compilateur en un numéro de ligne et un nom de fichier donnés.

## <a name="syntax"></a>Syntaxe

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>Notes

Le compilateur utilise le numéro de ligne et le nom de fichier facultatif pour faire référence aux erreurs qu’il trouve pendant la compilation. Le numéro de ligne fait généralement référence à la ligne d’entrée en cours et le nom de fichier fait référence au fichier d’entrée en cours. Le numéro de ligne est incrémenté après le traitement de chaque ligne.

La valeur *de la séquence digit* peut être n’importe quelle constante entière. Le remplacement de macro peut être effectué sur les jetons de prétraitement, mais le résultat doit correspondre à la syntaxe correcte. Le *nom de fichier* peut être n’importe quelle combinaison de caractères et doit être placé entre`" "`guillemets doubles (). Si *filename* est omis, le nom de fichier précédent reste inchangé.

Vous pouvez modifier le numéro de ligne source et le nom de fichier en écrivant une directive **#line** . Le traducteur utilise le numéro de ligne et le nom de fichier pour déterminer les valeurs des macros `__FILE__` prédéfinies et `__LINE__`. Vous pouvez utiliser ces macros pour insérer des messages d’erreur auto-descriptifs dans le texte du programme. Pour plus d’informations sur ces macros prédéfinies, consultez [macros prédéfinies](../preprocessor/predefined-macros.md).

La `__FILE__` macro se développe en une chaîne dont le contenu est le nom de fichier, entouré par des guillemets doubles (`" "`).

Si vous modifiez le numéro de ligne et le nom de fichier, le compilateur ignore les valeurs précédentes et continue le traitement avec les nouvelles valeurs. La directive **#line** est généralement utilisée par les générateurs de programmes pour faire en sorte que les messages d’erreur fassent référence au fichier source d’origine au lieu du programme généré.

Les exemples suivants illustrent **#line** et `__LINE__` les `__FILE__` macros et.

Dans cette instruction, le numéro de ligne stocké en interne est défini sur 151 et le nom de fichier est remplacé par Copy. c.

```C
#line 151 "copy.c"
```

Dans cet exemple, la macro `ASSERT` utilise les `__LINE__` macros prédéfinies et `__FILE__` pour imprimer un message d’erreur sur le fichier source si une assertion donnée n’a pas la valeur true.

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
