---
title: Macros (C/C++)
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: ba2c0f012974a528876219d00c61c0f31a6cd820
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218864"
---
# <a name="macros-cc"></a>Macros (C/C++)

Le préprocesseur étend les macros dans toutes les lignes à l’exception des *directives*de préprocesseur, les **#** lignes qui ont un comme premier caractère autre qu’un espace blanc. Il étend les macros dans certaines directives qui ne sont pas ignorées dans le cadre d’une compilation conditionnelle. Les *directives de compilation conditionnelle* vous permettent de supprimer la compilation des parties d’un fichier source. Ils testent une expression ou un identificateur constant pour déterminer les blocs de texte à passer au compilateur et ceux à supprimer du fichier source pendant le prétraitement.

La directive `#define` est généralement utilisée pour associer des identificateurs explicites à des constantes, à des mots clés, ainsi qu'à des instructions et des expressions couramment utilisées. Les identificateurs qui représentent des constantes sont parfois appelés constantes symboliques ou *constantes manifestes*. Les identificateurs qui représentent des instructions ou desexpressions sont appelés macros. Dans cette documentation relative aux préprocesseurs, seul le terme « macro » est utilisé.

Lorsque le nom d’une macro est reconnu dans le texte de la source du programme ou dans les arguments de certaines autres commandes de préprocesseur, il est traité comme un appel à cette macro. Le nom de la macro est remplacé par une copie du corps de la macro. Si la macro accepte des arguments, les arguments réels suivant le nom de la macro sont substitués aux paramètres formels dans le corps de la macro. Le processus de remplacement d’un appel de macro par la copie traitée du corps est appelé *expansion* de l’appel de macro.

En pratique, il existe deux types de macro. *Les macros de type objet* ne prennent pas d’arguments. Les macros de *type fonction* peuvent être définies pour accepter des arguments, afin qu’elles s’affichent et agissent comme des appels de fonction. Étant donné que les macros ne génèrent pas d’appels de fonction réels, vous pouvez parfois exécuter des programmes plus rapidement en remplaçant les appels de fonction par des macros. (En C++, les fonctions inline sont souvent une méthode conseillée.) Toutefois, les macros peuvent créer des problèmes si vous ne les définissez pas et ne les utilisez pas avec précaution. Vous devrez peut-être utiliser des parenthèses dans les définitions de macros avec des arguments afin de conserver la priorité appropriée dans une expression. En outre, il est possible que les macros ne gèrent pas correctement les expressions avec effets secondaires. Pour plus d’informations, consultez `getrandom` l’exemple de [la directive #define](../preprocessor/hash-define-directive-c-cpp.md).

Une fois que vous avez défini une macro, vous ne pouvez pas la redéfinir sur une valeur différente sans supprimer au préalable la définition d’origine. Toutefois, vous pouvez la redéfinir avec exactement la même définition. Par conséquent, la même définition peut apparaître plusieurs fois dans un programme.

La `#undef` directive supprime la définition d’une macro. Une fois que vous avez supprimé la définition, vous pouvez redéfinir la macro sur une valeur différente. [La directive #define](../preprocessor/hash-define-directive-c-cpp.md) et [la directive #undef](../preprocessor/hash-undef-directive-c-cpp.md) décrivent `#define` les `#undef` directives et, respectivement.

Pour plus d'informations, consultez

- [Macros et C++](../preprocessor/macros-and-cpp.md)

- [Macros variadiques](../preprocessor/variadic-macros.md)

- [Macros prédéfinies](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>Voir aussi

[Référence duC++ préprocesseur C/](../preprocessor/c-cpp-preprocessor-reference.md)
