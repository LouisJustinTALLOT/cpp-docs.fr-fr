---
title: '/ Zc : wchar_t (wchar_t est un Type natif) | Documents Microsoft'
ms.custom: ''
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 061aa4a70412a0b51450470e690bea5633b764ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381279"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t est un type natif)

Analysez `wchar_t` en tant que type intégré selon la norme C++.

## <a name="syntax"></a>Syntaxe

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>Notes

Si **/Zc :** est activé, `wchar_t` est un mot clé pour un type intégral intégré dans le code compilé en C++. Si **/Zc:wchar_t-** (avec un signe moins) est spécifié, ou dans le code compilé en C, `wchar_t` n’est pas un type intégré. Au lieu de cela, `wchar_t` est défini comme un `typedef` pour `unsigned short` dans l’en-tête canonique stddef.h. (L’implémentation Microsoft définit dans un autre en-tête est inclus par stddef.h et d’autres en-têtes standards.)

Nous ne recommandons pas **/Zc:wchar_t-** , car la norme C++ requiert que `wchar_t` être un type intégré. L'utilisation de la version `typedef` peut entraîner des problèmes de portabilité. Si vous mettez à niveau des versions antérieures de Visual C++ et rencontrez l’erreur du compilateur [l’erreur C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) parce que le code tente de convertir implicitement un `wchar_t` à `unsigned short`, nous vous recommandons de modifier le code pour corriger cette erreur, à la place paramètre **/Zc:wchar_t-**.

Le **/Zc :** option est activée par défaut dans les compilations C++ et est ignorée dans les compilations C. Le [/ permissive-](permissive-standards-conformance.md) option n’affecte pas **/Zc :**.

Microsoft implémente `wchar_t` en tant que valeur non signée de deux octets. Il est mappé avec le type natif spécifique à Microsoft `__wchar_t`. Pour plus d’informations sur `wchar_t`, consultez [plages de types de données](../../cpp/data-type-ranges.md) et [Types fondamentaux](../../cpp/fundamental-types-cpp.md).

Si vous écrivez un nouveau code qui doit interagir avec l’ancien code qui utilise toujours le `typedef` version de `wchar_t`, vous pouvez fournir des surcharges pour les deux le `unsigned short` et `__wchar_t` variantes de `wchar_t`, de sorte que votre code peut être lié à le code compilé avec **/Zc :** ou code compilé sans lui. Sinon, vous devez fournir deux builds différentes de la bibliothèque, une avec et sans **/Zc :** activé. Même dans ce cas, nous vous recommandons de générer le code plus ancien à l'aide du compilateur que vous utilisez pour compiler le nouveau code. Ne mélangez jamais les binaires compilés avec des compilateurs distincts.

Lorsque **/Zc :** est spécifié,  **\_WCHAR\_T\_défini** et  **\_natif\_WCHAR\_T\_défini** symboles qui sont définis. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).

Si votre code utilise les fonctions globales COM du compilateur, car **/Zc :** est maintenant sur par défaut, nous vous recommandons de modifier les références explicites à comsupp.lib (à partir de la [commentaire pragma](../../preprocessor/comment-c-cpp.md) ou sur le ligne de commande) par omsuppw.lib ou comsuppwd.lib. (Si vous devez compiler avec **/Zc:wchar_t-**, utilisez comsupp.lib.) Si vous incluez le fichier d'en-tête comdef.h, la bibliothèque appropriée est automatiquement spécifiée. Pour plus d’informations sur la prise en charge COM du compilateur, consultez [Support COM du compilateur](../../cpp/compiler-com-support.md).

Le `wchar_t` type intégré n’est pas pris en charge lorsque vous compilez du code C. Pour plus d’informations sur les problèmes de conformité avec Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **langage** page.

1. Modifier la **traitement de wchar_t en tant que Type intégré** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
