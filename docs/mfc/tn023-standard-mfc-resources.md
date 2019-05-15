---
title: 'TN023 : Ressources MFC standard'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: b6a1978a92fcf53de7caacd41c01a91ff16a3fc3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611404"
---
# <a name="tn023-standard-mfc-resources"></a>TN023 : Ressources MFC standard

Cette note décrit les ressources standard fournies et requises par la bibliothèque MFC.

## <a name="standard-resources"></a>Ressources standard

MFC propose deux catégories de ressources prédéfinies que vous pouvez utiliser dans votre application : ressources image clipart et ressources framework standard.

Les ressources image clipart sont des ressources supplémentaires auxquelles le framework ne dépend, mais que vous pouvez souhaiter ajouter à l'interface utilisateur de l'application. Les ressources image clipart suivantes figurent dans l’exemple général MFC [CLIPART](../overview/visual-cpp-samples.md):

- Common.rc : Un seul fichier de ressources qui contient :

   - Une grande collection d’icônes qui représentent une variété de tâches d’entreprise et de traitement de données.

   - Plusieurs curseurs communs (voir aussi l'Afxres.rc).

   - Bitmap de la barre d'outils qui contient plusieurs boutons de la barre d'outils.

   - Ressources bitmap et icône utilisées par Commdlg.dll.

- Indicate.rc : Contient des ressources de chaîne pour les indicateurs d’état de la clé de barre d’état, tels que « CAP » pour le verrouillage des majuscules.

- Prompts.rc : Contient des ressources de chaîne d’invite de menu pour chaque commande prédéfinie, par exemple « Créer un nouveau document » pour ID_FILE_NEW.

- COMMDLG.rc : Un fichier .rc compatible Visual C++ qui contient les modèles de boîte de dialogue COMMDLG standards.

Les ressources framework standard sont des ressources avec des ID AFX auxquelles le framework dépend pour les implémentations internes. Vous devez fréquemment modifier ces ressources AFX. Dans ce cas, vous devrez suivre la procédure dont les grandes lignes sont présentées plus loin dans cette rubrique.

Les ressources framework suivantes sont contenues dans le répertoire MFC\INCLUDE :

- AFXRES.rc : Ressources communes utilisées par l’infrastructure.

- Afxprint.rc : Ressources spécifiques à l’impression.

- AFXOLECL.rc : Ressources spécifiques aux applications clientes OLE.

- Afxolev.rc : Ressources spécifiques aux applications serveur OLE complètes.

## <a name="using-clip-art-resources"></a>Utilisation des ressources image clipart

#### <a name="to-use-a-clip-art-binary-resource"></a>Pour utiliser une ressource binaire d'image clipart

1. Ouvrez le fichier des ressources de votre application dans Visual C++.

1. Ouvrez Common.rc. Ce fichier contient toutes les ressources d'image clipart binaires. Cette opération peut prendre quelque temps car le fichier Common.rc est compilé.

1. Maintenez la touche CTRL enfoncée pendant que vous faites glisser les ressources à utiliser dans Common.rc vers le fichier des ressources de votre application.

Pour utiliser d'autres ressources image clipart, suivez les mêmes étapes. La seule différence est que vous ouvrirez le fichier .rc approprié au lieu du fichier Common.rc.

> [!NOTE]
>  Faites attention de ne pas déplacer involontairement des ressources en dehors du fichier Common.rc de manière irréversible. Si vous maintenez la touche CTRL enfoncée pendant que vous faites glisser des ressources, vous allez créer une copie. Si vous ne conservez pas la touche CTRL enfoncée pendant que vous effectuez le déplacement des éléments, les ressources seront déplacées. Si vous avez modifié le fichier Common.rc par inadvertance, cliquez sur "Non" lorsque vous êtes invité à enregistrer les modifications apportées au fichier Common.rc.

> [!NOTE]
>  Les fichiers de ressources .rc contiennent une ressource TEXTINCLUDE spéciale qui vous empêche d’écraser par erreur les fichiers .rc standard.

### <a name="customizing-standard-framework-resources"></a>Personnalisation des ressources framework standard

Les ressources framework standard sont généralement incluses dans une application avec la commande #include dans le fichier de ressources d'une application. AppWizard génère un fichier de ressources. Ce fichier contient les ressources framework standard adéquates, en fonction des options AppWizard que vous sélectionnez. Vous pouvez examiner, ajouter ou supprimer les ressources incluses en modifiant les directives au moment de la compilation. Pour ce faire, ouvrez le **ressource** menu et sélectionnez **Set Includes**. Recherchez l'élément de modification "Compile-Time Directives". Exemple :

```
#include "afxres.rc"
#include "afxprint.rc"
```

Le cas le plus fréquent de personnalisation des ressources framework standard est l'ajout ou la suppression des inclusions supplémentaires pour l'impression, le client OLE et la prise en charge du serveur OLE.

Dans certains cas exceptionnels, vous pouvez personnaliser le contenu des ressources framework standard pour votre application spécifique, pas seulement pour ajouter et supprimer le fichier complet. Les étapes suivantes montrent comment vous pouvez limiter les ressources qui sont incluses :

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Pour personnaliser le contenu d'un fichier de ressources standard

1. Ouvrez le fichier de ressources dans Visual C++.

1. Lors de l'utilisation de la commande Set Includes relative aux ressources, supprimez `#include` dans le fichier standard .rc que vous souhaitez personnaliser. Par exemple, pour personnaliser la barre d'outils d'aperçu avant impression, supprimez la ligne `#include "afxprint.rc"`.

1. Ouvrez les fichiers de ressources standard appropriés dans MFC\INCLUDE. Suite au dernier exemple de cette rubrique, le fichier approprié est MFC\Include\Aafxprint.rc

1. Copiez toutes les ressources du fichier .rc standard dans votre fichier de ressources d'application.

1. Modifiez la copie des ressources standard dans votre fichier de ressources d'application.

> [!NOTE]
>  Ne modifiez pas les ressources directement dans les fichiers .rc standard. Ce qui modifie les ressources disponibles dans chaque application, et non dans celle sur laquelle vous travaillez actuellement.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
