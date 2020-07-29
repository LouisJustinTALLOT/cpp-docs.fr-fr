---
title: /Zc:wchar_t (wchar_t est un type natif)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 114ed4a279b66571c0dc81fc1139dcdc59c17eae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234313"
---
# <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t est un type natif)

Analyser **`wchar_t`** en tant que type intégré en fonction de la norme C++.

## <a name="syntax"></a>Syntaxe

> **/Zc : wchar_t**[ **-** ]

## <a name="remarks"></a>Notes

Si **/Zc : wchar_t** est activé, **`wchar_t`** est un mot clé pour un type intégral intégré dans le code compilé en C++. Si **/Zc : wchar_t-** (avec un signe moins) est spécifié, ou dans le code compilé en tant que C, **`wchar_t`** n’est pas un type intégré. À la place, **`wchar_t`** est défini en tant que **`typedef`** pour **`unsigned short`** dans l’en-tête canonique STDDEF. h. (L’implémentation Microsoft le définit dans un autre en-tête qui est inclus par STDDEF. h et d’autres en-têtes standard.)

Nous vous déconseillons d’utiliser **/Zc : wchar_t** , car la norme C++ nécessite que **`wchar_t`** soit un type intégré. L’utilisation de la **`typedef`** version peut entraîner des problèmes de portabilité. Si vous effectuez une mise à niveau à partir de versions antérieures de Visual Studio et que vous rencontrez une erreur du compilateur [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) , car le code tente de convertir implicitement un **`wchar_t`** en **`unsigned short`** , nous vous recommandons de modifier le code pour corriger l’erreur, au lieu de définir **/Zc : wchar_t-**.

L’option **/Zc : wchar_t** est activée par défaut dans les compilations C++ et est ignorée dans les compilations C. L’option [/permissive-](permissive-standards-conformance.md) n’a pas d’incidence sur **/Zc : wchar_t**.

Microsoft implémente **`wchar_t`** en tant que valeur non signée sur deux octets. Il correspond au type natif spécifique à Microsoft **`__wchar_t`** . Pour plus d’informations sur **`wchar_t`** , consultez plages de types de [données](../../cpp/data-type-ranges.md) et [types fondamentaux](../../cpp/fundamental-types-cpp.md).

Si vous écrivez un nouveau code qui doit interagir avec du code plus ancien qui utilise toujours la **`typedef`** version de **`wchar_t`** , vous pouvez fournir des surcharges pour **`unsigned short`** les **`__wchar_t`** variantes et de **`wchar_t`** , afin que votre code puisse être lié au code compilé avec **/Zc : wchar_t** ou le code compilé sans lui. Sinon, vous devez fournir deux builds différentes de la bibliothèque, l’une avec et l’autre sans **/Zc : wchar_t** activé. Même dans ce cas, nous vous recommandons de générer le code plus ancien à l'aide du compilateur que vous utilisez pour compiler le nouveau code. Ne mélangez jamais les binaires compilés avec des compilateurs distincts.

Quand **/Zc : wchar_t** est spécifié, les symboles définis par ** \_ WCHAR \_ t \_ défini** et ** \_ natives de \_ WCHAR \_ t \_ ** sont définis. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).

Si votre code utilise les fonctions globales COM du compilateur, car **/Zc : wchar_t** est désormais activé par défaut, nous vous recommandons de modifier les références explicites à COMSUP. lib (à partir du [pragma de commentaire](../../preprocessor/comment-c-cpp.md) ou sur la ligne de commande) en comsuppw. lib ou comsuppwd. lib. (Si vous devez compiler avec **/Zc : wchar_t-**, utilisez COMSUP. lib.) Si vous incluez le fichier d’en-tête ComDef. h, la bibliothèque appropriée est spécifiée. Pour plus d’informations sur la prise en charge COM du compilateur, consultez [prise en charge du compilateur com](../../cpp/compiler-com-support.md).

Le **`wchar_t`** type intégré n’est pas pris en charge quand vous compilez du code C. Pour plus d’informations sur les problèmes de conformité avec Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page **Propriétés de configuration**  >  **C/C++**  >  **Language** .

1. Modifiez la propriété **Treat wchar_t en tant que type intégré** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)<br/>
