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
ms.openlocfilehash: ba0224d166795b34d636ace610265e115209e49c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358860"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Source de données : configuration d'une source de données ODBC par programme

Ce sujet explique comment vous pouvez configurer les noms de source de données Open Database Connectivity (ODBC) programmatiquement. Cela vous donne la flexibilité d’accéder aux données sans forcer l’utilisateur à utiliser explicitement l’administrateur ODBC ou d’autres programmes pour spécifier les noms des sources de données.

En règle générale, un utilisateur exécute l’administrateur d’ODBC pour créer une source de données si le système de gestion de base de données associé (DBMS) prend en charge cette opération.

Lors de la création d’une source de données Microsoft Access ODBC par l’intermédiaire de l’administrateur ODBC, vous avez deux choix : vous pouvez sélectionner un fichier .mdb existant ou vous pouvez créer un nouveau fichier .mdb. Il n’existe aucun moyen programmatique de créer le fichier .mdb à partir de votre application MFC ODBC. Par conséquent, si votre application exige que vous placez des données dans une source de données Microsoft Access (.mdb fichier), vous souhaitez très probablement avoir un fichier .mdb vide que vous pouvez utiliser ou copier chaque fois que vous en avez besoin.

Cependant, de nombreux DBMS permettent la création de sources de données programmatiques. Certaines sources de données conservent une spécification d’annuaire pour les bases de données. Autrement dit, un répertoire est la source de données et chaque tableau dans la source de données est stocké dans un fichier séparé (dans le cas de dBASE, chaque table est un fichier .dbf). Les conducteurs d’autres bases de données ODBC, tels que Microsoft Access et SQL Server, exigent que certains critères spécifiques soient remplis avant qu’une source de données puisse être établie. Par exemple, lorsque vous utilisez le conducteur SQL Server ODBC, vous devez avoir établi un ordinateur SQL Server.

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>SQLConfigDataSource Exemple

L’exemple suivant `::SQLConfigDataSource` utilise la fonction API ODBC pour créer une nouvelle source de données Excel appelée New Excel Data Source :

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Notez que la source de données est en fait un répertoire (C: EXCELDIR); ce répertoire doit exister. Le pilote Excel utilise les répertoires comme sources de données et fichiers comme tableaux individuels (une table par fichier .xls).

Pour plus d’informations sur la création de tableaux, voir [Source de données : Création programmatique d’une table dans une source de données ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Les informations suivantes discutent des paramètres qui `::SQLConfigDataSource` doivent être transmis à la fonction API ODBC. Pour `::SQLConfigDataSource`utiliser, vous devez inclure le fichier d’en-tête Odbcinst.h et utiliser la bibliothèque d’importation Odbcinst.lib. En outre, Odbccp32.dll doit être dans le chemin à l’heure de course (ou Odbcinst.dll pour 16 bits).

Vous pouvez créer un nom source de données ODBC à l’aide d’un administrateur ODBC ou d’un utilitaire similaire. Cependant, il est parfois souhaitable de créer un nom de source de données directement à partir de votre application pour obtenir l’accès sans exiger de l’utilisateur d’exécuter un utilitaire distinct.

L’administrateur d’ODBC (généralement installé dans le panneau de contrôle) crée une nouvelle source de données en plaçant des entrées dans le registre Windows (ou, pour 16 bits, dans le fichier Odbc.ini). Le gestionnaire de chauffeur de l’ODBC interroge ce dossier pour obtenir les renseignements requis sur la source de données. Il est important de savoir quelles informations doivent être placées dans le `::SQLConfigDataSource`registre parce que vous devez lui fournir l’appel à .

Bien que ces informations puissent être `::SQLConfigDataSource`écrites directement au registre sans l’utiliser, toute application qui le fait repose sur la technique actuelle utilisée par le gestionnaire de conducteur pour maintenir ses données. Si une révision ultérieure de l’ODBC Driver Manager implémente la tenue de dossiers sur les sources de données d’une manière différente, toute application qui utilise cette technique est cassée. Il est généralement conseillé d’utiliser une fonction API lorsque l’on est fourni. Par exemple, votre code est portable de 16 bits `::SQLConfigDataSource` à 32 bits si vous utilisez la fonction, parce que la fonction écrit correctement au fichier Odbc.ini ou au registre.

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>Paramètres SQLConfigDataSource

Ce qui suit explique `::SQLConfigDataSource` les paramètres de la fonction. Une grande partie de l’information provient de la *référence du programmeur* API de l’ODBC fournie avec la version 1.5 visuelle et plus tard.

### <a name="function-prototype"></a><a name="_core_function_prototype"></a>Prototype de fonction

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Notes

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>Paramètres et utilisation

*hwndParent*<br/>
La fenêtre spécifiée comme propriétaire de toutes les boîtes de dialogue que le gestionnaire de pilote ODBC ou le pilote spécifique ODBC crée pour obtenir des informations supplémentaires de l’utilisateur sur la nouvelle source de données. Si le *paramètre lpszAttributes* ne fournit pas suffisamment d’informations, une boîte de dialogue apparaît. Le *paramètre hwndParent* peut être NULL.

*lpszDriver (en)*<br/>
La description du conducteur. C’est le nom présenté aux utilisateurs plutôt que le nom du conducteur physique (le DLL).

*lpszAttributes*<br/>
Liste des attributs sous la forme de "keyname-value". Ces cordes sont séparées par des terminateurs nuls avec deux terminateurs nuls consécutifs à la fin de la liste. Ces attributs sont principalement des entrées spécifiques au conducteur par défaut, qui entrent dans le registre pour la nouvelle source de données. Une clé importante qui n’est pas mentionnée dans la référence ODBC API pour cette fonction est "DSN" ("nom source de données"), qui spécifie le nom de la nouvelle source de données. Le reste des entrées sont spécifiques au conducteur pour la nouvelle source de données. Souvent, il n’est pas nécessaire de fournir toutes les entrées parce que le pilote peut inciter l’utilisateur avec des boîtes de dialogue pour les nouvelles valeurs. (Définissez *hwndParent* à NULL pour causer ceci.) Vous pouvez fournir explicitement des valeurs par défaut afin que l’utilisateur ne soit pas invité.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Déterminer la description d’un pilote pour le paramètre lpszDriver à l’aide de l’administrateur ODBC

1. Exécuter l’administrateur ODBC.

1. Cliquez sur **Add**.

Cela vous donne une liste de pilotes installés et leurs descriptions. Utilisez cette description comme paramètre *lpszDriver.* Notez que vous utilisez l’ensemble de la description, comme "Excel Files (.xls)", y compris l’extension du nom de fichier et les parenthèses si elles existent dans la description.

Comme alternative, vous pouvez examiner le registre (ou, pour 16 bits, le fichier Odbcinst.ini), qui contient une liste de toutes les entrées et descriptions du pilote sous la clé du registre "ODBC Drivers" (ou la section [ODBC Drivers] dans Ocinst.ini).

Une façon de trouver les noms de clés et les valeurs pour le paramètre *lpszAttributes* est d’examiner le fichier Odbc.ini pour une source de données déjà configurée (peut-être celle qui a été configurée par oDBC Administrateur).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Trouver des noms de clés et des valeurs pour le paramètre lpszAttributes

1. Exécutez l’éditeur du registre Windows (ou, pour 16 bits, ouvrez le fichier Odbc.ini).

1. Trouvez les informations sur les sources de données de l’ODBC à l’aide de l’une des suivantes :

   - Pour 32 bits, trouvez la clé **HKEY_CURRENT_USER-Logiciel-ODBC-ODBC. Sources de données INI-ODBC** dans la vitre gauche.

      Le volet droit répertorie les entrées du formulaire: "pub: REG_SZ:*\<nom source de données>*", où * \<le nom de source de données>* est une source de données qui a déjà été configuré avec les paramètres souhaités pour le pilote que vous avez l’intention d’utiliser. Sélectionnez la source de données que vous souhaitez, par exemple, SQL Server. Les articles suivant la chaîne "pub:" sont, dans l’ordre, le nom de clé et la valeur à utiliser dans votre paramètre *lpszAttributes.*

   - Pour 16 bits, trouver la section dans le fichier Odbc.ini marqué par*\<[nom source de données>*].

      Les lignes suivant cette ligne sont de la forme "keyname-value". Ce sont exactement les entrées à utiliser dans votre paramètre *lpszAttributes.*

Vous pouvez également examiner la documentation pour le pilote spécifique que vous allez utiliser. Vous pouvez trouver des informations utiles dans l’aide en ligne pour le conducteur, que vous pouvez accéder en exécutant oDBC Administrateur. Ces fichiers d’aide sont généralement placés dans l’annuaire WINDOWS-SYSTEM pour Windows NT, Windows 3.1 ou Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Pour obtenir de l’aide en ligne pour votre chauffeur ODBC

1. Exécuter l’administrateur ODBC.

1. Cliquez sur **Add**.

1. Sélectionnez le nom du conducteur.

1. Cliquez sur **OK**.

Lorsque l’administrateur d’ODBC affiche les informations pour créer une nouvelle source de données pour ce pilote particulier, cliquez sur **Aide**. Cela ouvre le fichier d’aide pour ce conducteur particulier, qui contient généralement des informations importantes concernant l’utilisation du conducteur.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)
