# FluentDb
Fluent interface for db class


/* Exemple 1 */
string sql = "select * from table";
DataTable dataTable = Db.SetSql(sql).GetDataTable();


/* Exemple 2 with parameters */
sql = "select @id, @name from table";
List<SqlParameter> sqlParameters = new List<SqlParameter>();

SqlParameter parameter = new SqlParameter("@id", SqlDbType.Int) {
    Value = "id"
};
sqlParameters.Add(parameter);

SqlParameter parameter2 = new SqlParameter("@name", SqlDbType.NVarChar) {
    Value = "name"
};
sqlParameters.Add(parameter2);

dataTable = Db.SetSql(sql).GetDataTable("", sqlParameters);


/* Exemple 3 */
string name = Db.Prepare()
                .GetScalaire("select name from table")
                .ToString();
