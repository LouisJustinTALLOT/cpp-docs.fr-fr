---
title: "Source de données : configuration d'une source de données ODBC par programme"
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: 3d02a19d6c61e79fffd31b67ef1b8f7ea9007fcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677368"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Source de données : configuration d'une source de données ODBC par programme

Cette rubrique explique comment vous pouvez configurer des noms de source de données Open Database Connectivity (ODBC) par programmation. Cela vous donne une flexibilité pour accéder aux données sans forcer l’utilisateur à utiliser explicitement l’administrateur ODBC ou autres programmes pour spécifier les noms de sources de données.

En règle générale, un utilisateur exécute l’administrateur ODBC pour créer une source de données si le système de gestion de base de données associée (SGBD) prend en charge cette opération.

Lorsque vous créez une source de données ODBC Microsoft Access via l’administrateur ODBC, vous disposez de deux options : vous pouvez sélectionner un fichier .mdb existant ou vous pouvez créer un nouveau fichier .mdb. Il n’existe aucun moyen de programmation de la création du fichier .mdb à partir de votre application ODBC MFC. Par conséquent, si votre application nécessite de placer des données dans une source de données Microsoft Access (fichier .mdb), vous aurez probablement souhaitez avoir un fichier .mdb vide que vous pouvez utiliser ou copier lorsque vous en avez besoin.

Toutefois, nombreux SGBD permettre de créer une source de données par programmation. Certaines sources de données conservent une spécification de répertoire pour les bases de données. Autrement dit, un répertoire est la source de données et chaque table de la source de données est stockée dans un fichier séparé (dans le cas de dBASE, chaque table est un fichier .dbf). Pilotes d’autres bases de données ODBC, telles que Microsoft Access et SQL Server, nécessitent que certains critères spécifiques soient remplis avant l’établissement d’une source de données. Par exemple, lorsque vous utilisez le pilote ODBC de SQL Server, vous devez avoir établi un ordinateur SQL Server.

##  <a name="_core_sqlconfigdatasource_example"></a> Exemple de SQLConfigDataSource

L’exemple suivant utilise le `::SQLConfigDataSource` fonction API ODBC pour créer une nouvelle source de données Excel appelé nouvelle Source de données Excel :

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Notez que la source de données est en réalité un répertoire (C:\EXCELDIR) ; ce répertoire doit exister. Le pilote Excel utilise les répertoires comme ses sources de données et les fichiers comme des tables individuelles (une table par fichier .xls).

Pour plus d’informations sur la création de tables, consultez [Source de données : création d’une Table dans une Source de données ODBC par programmation](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Les informations suivantes décrivent les paramètres qui doivent être transmis à la `::SQLConfigDataSource` fonction API ODBC. Pour utiliser `::SQLConfigDataSource`, vous devez inclure le fichier d’en-tête Odbcinst.h et utiliser la bibliothèque d’importation Odbcinst.lib. En outre, Odbccp32.dll doit se trouver dans le chemin d’accès au moment de l’exécution (ou Odbcinst.dll pour les plateformes 16 bits).

Vous pouvez créer un nom de source de données ODBC à l’aide de l’administrateur ODBC ou un utilitaire similaire. Toutefois, il est parfois souhaitable de créer un nom de source de données directement à partir de votre application pour obtenir l’accès sans que l’utilisateur à exécuter un utilitaire distinct.

Administrateur ODBC (installé généralement dans le panneau de configuration) crée une nouvelle source de données en ajoutant des entrées dans le Registre Windows (ou, pour les plateformes 16 bits, dans le fichier Odbc.ini). Le Gestionnaire de pilote ODBC interroge ce fichier pour obtenir les informations requises sur la source de données. Il est important de savoir quelles informations doivent être placées dans le Registre, car vous devrez lui fournir l’appel à `::SQLConfigDataSource`.

Bien que ces informations peuvent être écrit directement dans le Registre sans utiliser `::SQLConfigDataSource`, toute application qui fait repose sur la technique actuelle utilisée par le Gestionnaire de pilote pour conserver ses données. Si une version ultérieure pour la Gestionnaire de pilotes ODBC implémente consignation sur les sources de données d’une façon différente, toute application qui utilise cette technique est interrompue. Il est généralement conseillé d’utiliser une fonction API lorsqu’elle est fournie. Par exemple, votre code est portable à partir de 16 bits jusqu'à 32 bits si vous utilisez le `::SQLConfigDataSource` fonctionner, car la fonction écrit correctement dans le fichier Odbc.ini ou dans le Registre.

##  <a name="_core_sqlconfigdatasource_parameters"></a> Paramètres de SQLConfigDataSource

Décrit les paramètres de la `::SQLConfigDataSource` (fonction). La plupart des informations provient de l’API ODBC *de référence du programmeur* fourni avec Visual C++ version 1.5 et versions ultérieure.

###  <a name="_core_function_prototype"></a> Prototype de fonction

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Notes

####  <a name="_core_parameters_and_usage"></a> Paramètres et utilisation

*hwndParent*<br/>
La fenêtre spécifiée en tant que propriétaire de toutes les boîtes de dialogue que le Gestionnaire de pilotes ODBC ou le pilote ODBC spécifique crée pour obtenir des informations supplémentaires à partir de l’utilisateur sur la nouvelle source de données. Si le *lpszAttributes* paramètre ne fournit pas suffisamment d’informations, une boîte de dialogue s’affiche. Le *hwndParent* paramètre peut être NULL.

*lpszDriver*<br/>
Description du pilote. Il s’agit du nom présenté aux utilisateurs plutôt que le nom de pilote physique (la DLL).

*lpszAttributes*<br/>
Liste d’attributs sous la forme « keyname = value ». Ces chaînes sont séparées par des marques de fin null avec deux indicateurs de fin null consécutives à la fin de la liste. Ces attributs sont principalement entrées par défaut spécifiques au pilote, qui transitent dans le Registre pour la nouvelle source de données. Une clé importante qui n’est pas mentionnée dans la référence d’API ODBC pour cette fonction est « DSN » (« data source name »), qui spécifie le nom de la nouvelle source de données. Le reste des entrées sont spécifiques au pilote pour la nouvelle source de données. Souvent, il n’est pas nécessaire de fournir toutes les entrées, car le pilote peut inviter l’utilisateur avec les boîtes de dialogue pour les nouvelles valeurs. (Définissez *hwndParent* avec la valeur NULL à l’origine.) Vous souhaiterez peut-être fournir explicitement des valeurs par défaut afin que l’utilisateur n’est pas invité.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Pour déterminer la description d’un pilote pour le paramètre lpszDriver à l’aide de l’administrateur ODBC

1. Exécutez l’administrateur ODBC.

1. Cliquez sur **Ajouter**.

Cela vous donne une liste des pilotes installés et leurs descriptions. Utilisez cette description comme la *lpszDriver* paramètre. Notez que vous utilisez l’intégralité de la description, tels que « Fichiers Excel (*.xls) », y compris l’extension de nom de fichier et les parenthèses s’ils existent dans la description.

Comme alternative, vous pouvez examiner le Registre (ou, pour les plateformes 16 bits, le fichier Odbcinst.ini), qui contient une liste de toutes les entrées de pilote et des descriptions sous la clé de Registre « ODBC Drivers » (ou la section [ODBC Drivers] dans le fichier Odbcinst.ini).

Une façon de trouver les noms de clés et valeurs pour le *lpszAttributes* paramètre consiste à examiner le fichier Odbc.ini d’une source de données déjà configurée (peut-être celui qui a été configuré par l’administrateur ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Pour rechercher les noms de clés et valeurs du paramètre lpszAttributes

1. Exécutez l’Éditeur du Registre Windows (ou, pour les plateformes 16 bits, ouvrez le fichier Odbc.ini).

1. Rechercher les informations de sources de données ODBC à l’aide d’une des opérations suivantes :

   - Pour 32 bits, recherchez la clé **HKEY_CURRENT_USER\Software\ODBC\ODBC. Sources de données INI\ODBC** dans le volet gauche.

      Le volet droit répertorie les entrées au format : « pub : REG_SZ :*<data source name>*», où *<data source name>* est une source de données qui a déjà été configurée avec les paramètres souhaités pour le pilote que vous avez l’intention à utiliser. Sélectionnez la source de données, par exemple, SQL Server. Les éléments qui suivent la chaîne « pub : » sont, dans l’ordre, le nom de clé et la valeur à utiliser dans votre *lpszAttributes* paramètre.

   - Pour les plateformes 16 bits, recherchez la section dans le fichier Odbc.ini marqué par [*\<nom de source de données >*].

      Les lignes suivant cette ligne sont de la forme « keyname = value ». Il s’agit exactement les entrées à utiliser dans votre *lpszAttributes* paramètre.

Vous souhaiterez également examiner la documentation relative au pilote que vous vous apprêtez à utiliser. Vous trouverez des informations utiles dans l’aide en ligne pour le pilote, vous pouvez accéder en exécutant l’administrateur ODBC. Ces fichiers d’aide sont généralement placés dans le répertoire WINDOWS\SYSTEM pour Windows NT, Windows 3.1 ou Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Pour obtenir une aide en ligne pour votre pilote ODBC

1. Exécutez l’administrateur ODBC.

1. Cliquez sur **Ajouter**.

1. Sélectionnez le nom du pilote.

1. Cliquez sur **OK**.

Lorsque l’administrateur ODBC affiche les informations pour créer une nouvelle source de données pour ce pilote spécifique, cliquez sur **aide**. Cette opération ouvre le fichier d’aide pour ce pilote spécifique, qui contient généralement des informations importantes concernant l’utilisation du pilote.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)
