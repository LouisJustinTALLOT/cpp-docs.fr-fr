---
title: '#ligne de la Directive (C/C++) | Documents Microsoft'
ms.custom: ''
ms.date: 10/18/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#line'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ebbcea7432b27e9269b5041d90d14534a77b812
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839752"
---
# <a name="line-directive-cc"></a>#line, directive (C/C++)

Le `#line` directive indique au préprocesseur de modifier le numéro de ligne stocké en interne du compilateur et le nom de fichier à un numéro de ligne donné et le nom de fichier.

## <a name="syntax"></a>Syntaxe

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>Notes

Le compilateur utilise le numéro de ligne et le nom de fichier facultatif pour faire référence à des erreurs lors de la compilation. Le numéro de ligne fait généralement référence à la ligne d’entrée actuelle, et le nom de fichier fait référence au fichier d’entrée actuel. Le numéro de ligne est incrémenté après le traitement de chaque ligne.

Le *séquence de chiffres* valeur peut être une constante entière. Remplacement de macro peut être effectuée sur les jetons de prétraitement, mais le résultat doit correspondre à la syntaxe correcte. Le *nom de fichier* peut être n’importe quelle combinaison de caractères et doit être placée entre guillemets doubles (**» «**). Si *nom de fichier* est omis, le nom de fichier précédent demeure inchangée.

Vous pouvez modifier le numéro de ligne source et le nom de fichier en écrivant un `#line` la directive. Le convertisseur utilise le numéro de ligne et le nom de fichier pour déterminer les valeurs des macros prédéfinies **&#95; &#95;fichier&#95; &#95;** et **&#95; &#95;ligne&#95; &#95;**. Vous pouvez utiliser ces macros pour insérer des messages d’erreur autodescriptives dans le texte du programme. Pour plus d’informations sur ces macros prédéfinies, consultez [Macros prédéfinies](../preprocessor/predefined-macros.md).

Le **&#95; &#95;fichier&#95; &#95;** macro se développe en une chaîne dont le contenu est le nom de fichier, entouré de guillemets doubles (**» «**).

Si vous modifiez le numéro de ligne et le nom de fichier, le compilateur ignore les valeurs précédentes et continue le traitement avec les nouvelles valeurs. Le `#line` directive est généralement utilisée par les générateurs de programme pour générer des messages d’erreur faire référence au fichier source d’origine au lieu du programme généré.

Les exemples suivants illustrent `#line` et **&#95; &#95;ligne&#95; &#95;** et **&#95; &#95;fichier&#95; &#95;** macros.

Dans cette instruction, le numéro de ligne stocké en interne est défini à 151 et le nom de fichier est remplacé par copy.c.

```cpp
#line 151 "copy.c"
```

 Dans cet exemple, la macro `ASSERT` utilise les macros prédéfinies **&#95; &#95;ligne&#95; &#95;** et **&#95; &#95;fichier&#95; &#95;** pour imprimer une message d’erreur sur le fichier source si une assertion donnée n’est pas remplie.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)