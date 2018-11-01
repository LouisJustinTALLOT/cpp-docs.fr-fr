---
title: struct UNWIND_INFO
ms.date: 11/04/2016
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
ms.openlocfilehash: 0130d30c314a7736ffaf24753a2e6fdf9ad55b12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517037"
---
# <a name="struct-unwindinfo"></a>struct UNWIND_INFO

La structure d’informations de données de déroulement est utilisée pour enregistrer les effets de qu'une fonction a sur le pointeur de pile et où les registres non volatils sont enregistrés sur la pile :

|||
|-|-|
|UBYTE : 3|Version|
|UBYTE : 5|Indicateurs|
|UBYTE|Taille du prologue|
|UBYTE|Nombre de codes de déroulement|
|UBYTE : 4|Registre du frame|
|UBYTE : 4|Décalage de trame du Registre (mis à l’échelle)|
|USHORT \* n|Tableau de codes de déroulement|
|variable|Peut être de forme (1) ou (2) ci-dessous|

(1) Gestionnaire d’exceptions

|||
|-|-|
|ULONG|Adresse du Gestionnaire d’exceptions|
|variable|Données de gestionnaire spécifique au langage (facultatives)|

(2) chaînées informations de déroulement

|||
|-|-|
|ULONG|Adresse de début (fonction)|
|ULONG|Adresse de fin (fonction)|
|ULONG|Adresse des informations de déroulement|

La structure UNWIND_INFO doit être DWORD aligné en mémoire. La signification de chaque champ est la suivante :

- **Version**

   Numéro de version des données de déroulement, 1 actuellement.

- **indicateurs**

   Trois indicateurs sont actuellement définis :

   |Indicateur|Description|
   |-|-|
   |`UNW_FLAG_EHANDLER`| La fonction a un gestionnaire d’exceptions qui doit être appelé lors de la recherche pour les fonctions que vous avez besoin d’examiner les exceptions.|
   |`UNW_FLAG_UHANDLER`| La fonction a un gestionnaire de terminaisons qui doit être appelé lors du déroulement d’une exception.|
   |`UNW_FLAG_CHAININFO`| Cette structure n’est pas le principal pour la procédure d’informations de déroulement. Au lieu de cela, les informations de déroulement chaînées entrée est le contenu d’une entrée RUNTIME_FUNCTION antérieure. Consultez le texte suivant pour obtenir une explication de chaînées structures d’informations de déroulement. Si cet indicateur est défini, les indicateurs UNW_FLAG_EHANDLER et UNW_FLAG_UHANDLER doivent être effacées. En outre, les champs de d’allocation de Registre et de pile fixe frame doivent avoir les mêmes valeurs que dans le réplica principal d’informations de déroulement.|

- **Taille du prologue**

   Longueur du prologue de fonction en octets.

- **Nombre de codes de déroulement**

   Il s’agit du nombre d’emplacements dans le tableau de codes de déroulement. Notez que certains codes (par exemple, UWOP_SAVE_NONVOL) de déroulement nécessitent plusieurs emplacements dans le tableau.

- **Registre du frame**

   Si elle est différente de zéro, la fonction utilise un pointeur de frame, et ce champ est le nombre de Registre non volatil utilisé comme pointeur de frame, à l’aide de l’encodage même pour le champ d’information opération des nœuds UNWIND_CODE.

- **Registre du frame décalage (mis à l’échelle)**

   Si le champ du Registre du frame est différent de zéro, il s’agit de l’offset à l’échelle à partir de RSP qui s’applique au registre FP lorsqu’il est établi. Le registre FP réel a la valeur RSP + 16 \* ce nombre, autorisant des offsets compris entre 0 et 240. Cela permet de pointer vers le registre FP au milieu de l’allocation de pile locale pour les frames de pile dynamique, ce qui permet une meilleure densité de code via des instructions plus courtes (davantage d’instructions permettre utiliser le format d’offset signé 8 bits).

- **Tableau de codes de déroulement**

   Il s’agit d’un tableau d’éléments qui explique l’effet du prologue sur les registres non volatils et RSP. Consultez la section sur UNWIND_CODE pour la signification des différents éléments. À des fins d’alignement, ce tableau aura toujours un nombre pair d’entrées, avec la dernière entrée éventuellement inutilisée (auquel cas le tableau sera une plus longue que la valeur indiquée par le nombre de champs de codes de déroulement).

- **Adresse du Gestionnaire d’exceptions**

   Il s’agit d’un pointeur relatif à l’image au gestionnaire d’exception spécifique à la langue/arrêt de la fonction (si l’indicateur UNW_FLAG_CHAININFO est désactivé et un des indicateurs UNW_FLAG_EHANDLER ou UNW_FLAG_UHANDLER est défini).

- **Données du gestionnaire spécifique au langage**

   Il s’agit de données du Gestionnaire d’exception spécifique au langage de la fonction. Le format de ces données est non spécifié et complètement déterminé par le Gestionnaire d’exceptions spécifiques en cours d’utilisation.

- **Chaîne d’informations de déroulement**

   Si l’indicateur UNW_FLAG_CHAININFO est défini la structure UNWIND_INFO se termine par trois UWORD.  Ces UWORD représentent les informations RUNTIME_FUNCTION pour la fonction du déroulement chaîné.

## <a name="see-also"></a>Voir aussi

[Données de déroulement pour la gestion des exceptions et la prise en charge du débogueur](../build/unwind-data-for-exception-handling-debugger-support.md)