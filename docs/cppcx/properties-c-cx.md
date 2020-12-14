---
description: 'En savoir plus sur : propriétés (C++/CX)'
title: Propriétés (C++/CX)
ms.date: 01/22/2017
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
ms.openlocfilehash: 5c56dabb080404b074408f60b6c06535558c1d82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239712"
---
# <a name="properties-ccx"></a>Propriétés (C++/CX)

Les types de Windows Runtime exposent des données publiques sous forme de propriétés. Le code client accède à la propriété comme un DataMember public. En interne, la propriété est implémentée en tant que bloc qui contient une méthode d'accesseur get et une méthode d'accesseur set ou les deux. En utilisant des méthodes d'accesseur, vous pouvez exécuter des actions supplémentaires avant ou après avoir récupéré la valeur. Par exemple, vous pouvez déclencher un événement ou effectuer des contrôles de validation.

### <a name="remarks"></a>Notes

La valeur d'une propriété est contenue dans une variable privée, appelée *magasin de stockage*, qui est du même type que la propriété. Une propriété peut contenir un accesseur set, qui assigne une valeur au magasin de stockage et un accesseur get qui récupère la valeur du magasin de stockage. La propriété est en lecture seule si elle fournit uniquement un accesseur get, en écriture seule si elle fournit uniquement un accesseur set et en lecture/écriture (modifiable) si elle fournit les deux accesseurs.

Une propriété *triviale* est une propriété en lecture/écriture pour laquelle le compilateur implémente automatiquement les accesseurs et le magasin de stockage. Vous n'avez pas accès à l'implémentation du compilateur. Toutefois, vous pouvez déclarer une propriété personnalisée et déclarer explicitement ses accesseurs et son magasin de stockage. Dans un accesseur, vous pouvez exécuter toute logique dont vous avez besoin, par exemple valider l'entrée dans l'accesseur set, calculer une valeur d'après la valeur de propriété, accéder à une base de données ou déclencher un événement lorsque la propriété change.

Quand une classe ref C++/CX est instanciée, sa mémoire est initialisée à zéro avant que son constructeur ne soit appelé ; ainsi, toutes les propriétés reçoivent une valeur par défaut égale à zéro ou nullptr au moment de la déclaration.

### <a name="examples"></a>Exemples

L'exemple de code suivant illustre la procédure de déclaration et d'accès à une propriété. La première propriété, `Name`, est appelée propriété *triviale* car le compilateur génère automatiquement un accesseur `set` , un accesseur `get` et un magasin de stockage.

La deuxième propriété, `Doctor`, est une propriété en lecture seule car elle spécifie un *bloc Property* qui déclare explicitement un seul accesseur `get` . Étant donné que le bloc Property est déclaré, vous devez déclarer explicitement un magasin de stockage, c'est à-dire la variable String^ privée `doctor_`. En général, une propriété en lecture seule ne retourne que la valeur du magasin de stockage. Seule la classe elle-même peut définir la valeur du magasin de stockage, généralement dans le constructeur.

La troisième propriété, `Quantity`, est une propriété en lecture/écriture car elle déclare un bloc Property qui déclare un accesseur `set` et un accesseur `get` .

L'accesseur `set` réalise un test de validité défini par l'utilisateur sur la valeur assignée. Et, à la différence de C#, le mot *value* est ici juste l'identificateur du paramètre de l'accesseur `set` . Il ne s'agit pas d'un mot clé. Si *value* n'est pas supérieur à zéro, une exception Platform::InvalidArgumentException est levée. Sinon, le magasin de stockage, `quantity_`, est mis à jour avec la valeur assignée.

Notez qu'une propriété ne peut pas être initialisée dans une liste de membres. Vous pouvez évidemment initialiser les variables du magasin de stockage dans une liste de membres.

[!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]

## <a name="see-also"></a>Voir aussi

[Système de types](../cppcx/type-system-c-cx.md)<br/>
[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)
