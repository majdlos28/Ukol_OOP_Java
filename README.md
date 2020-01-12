# OOP Java program pro reprezentaci dotazu INSERT
code:
public class Query {
   
    public Query insert(String table){
        query = new StringBuilder();
        query.append("INSERT INTO ");
        query.append(table);
        return this;
    }

    public Query values(Object[] params){
        query.append(" VALUES(");

        int count = params.length;

        if(count == 0)
            throw new IllegalArgumentException("Neplatný počet parametrů");

        for (int i = 0; i<count; i++) {
            query.append("?,");
        }
        query.deleteCharAt(query.lastIndexOf(","));
        query.append(");");
        return this;
    }
}
