import React, { useState } from "react";

function App() {

  const [task, setTask] = useState("");
  const [tasks, setTasks] = useState([]);

  const addTask = () => {
    if(task !== ""){
      setTasks([...tasks, task]);
      setTask("");
    }
  };

  const deleteTask = (index) => {
    const newTasks = tasks.filter((task, i) => i !== index);
    setTasks(newTasks);
  };

  return (
    <div style={{textAlign:"center", marginTop:"50px"}}>
      <h1>Todo List</h1>

      <input
        type="text"
        placeholder="Enter task"
        value={task}
        onChange={(e)=>setTask(e.target.value)}
      />

      <button onClick={addTask}>Add</button>

      <ul>
        {tasks.map((t,index)=>(
          <li key={index}>
            {t}
            <button onClick={()=>deleteTask(index)}>Delete</button>
          </li>
        ))}
      </ul>

    </div>
  );
}

export default App;