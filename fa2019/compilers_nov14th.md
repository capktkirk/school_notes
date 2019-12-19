If Statement :

/*

 */
class IfStatement : public Statement {
  public:
    IfStatement(){}
    ~IfStatement(){}
    virutal void execute();
  private:
    Expression* ifcondition;
    Statement* ifbody;
    Statement* elsebody;
};

IfStatement(Expression* ifcondition, Statement* ifbody, Statement* elsebody)
  :ifcondition(ifcondition), ifbody(ifbody), elsebody(elsebody) {}

IfStatement(Expression* ifcondition, Statement* ifbody)
 : ifcondition(ifcondition), ifbody(ifbody), elsebody(nullptr) {}


IfStatement::~IfStatement(){
  delete ifcondition;
  delete ifbody;
  delete elsebody;
}

IfStatement::execute(){
  int cond = ifcondition->evaluate()->as_int();
  if(cond){
    ifbody->execute();
  }
  else if(elsebody){
    elsebody->execute();
  }
}


#######OR


IfStatement::execute(){
  int cond = ifcondition->evaluate()->as_int();
  if(cond){
    ifbody->execute();
  }
  else{
    elsebody->execute();
}


if_statement in GPL
{ $ = new IfStatement( $3, $5); }
{ $$ = new IfStatement($3, $5, $7); }


