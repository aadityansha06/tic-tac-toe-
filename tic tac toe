import React, { useState, useEffect } from 'react';

interface Player {
  name: string;
  mark: string;
}

interface Box {
  id: number;
  mark: string;
}

const TicTacToe = () => {
  const [players, setPlayers] = useState<Player[]>([]);
  const [boxes, setBoxes] = useState<Box[]>([
    { id: 1, mark: '' },
    { id: 2, mark: '' },
    { id: 3, mark: '' },
    { id: 4, mark: '' },
    { id: 5, mark: '' },
    { id: 6, mark: '' },
    { id: 7, mark: '' },
    { id: 8, mark: '' },
    { id: 9, mark: '' },
  ]);
  const [turn, setTurn] = useState<number>(0);
  const [winner, setWinner] = useState<string>('');
  const [gameOver, setGameOver] = useState<boolean>(false);

  useEffect(() => {
    const player1Name = prompt('Enter Player 1 name:');
    const player2Name = prompt('Enter Player 2 name:');
    const randomTurn = Math.floor(Math.random() * 2);
    setPlayers([
      { name: player1Name, mark: 'X' },
      { name: player2Name, mark: 'O' },
    ]);
    setTurn(randomTurn);
  }, []);

  const handleBoxClick = (id: number) => {
    if (gameOver) return;
    const newBoxes = boxes.map((box) => {
      if (box.id === id && box.mark === '') {
        box.mark = players[turn].mark;
      }
      return box;
    });
    setBoxes(newBoxes);
    checkWinner();
    setTurn((prevTurn) => (prevTurn === 0 ? 1 : 0));
  };

  const checkWinner = () => {
    const winningCombinations = [
      [1, 2, 3],
      [4, 5, 6],
      [7, 8, 9],
      [1, 4, 7],
      [2, 5, 8],
      [3, 6, 9],
      [1, 5, 9],
      [3, 5, 7],
    ];
    for (const combination of winningCombinations) {
      const marks = combination.map((id) => boxes.find((box) => box.id === id)?.mark);
      if (marks.every((mark) => mark === players[0].mark)) {
        setWinner(players[0].name);
        setGameOver(true);
        return;
      }
      if (marks.every((mark) => mark === players[1].mark)) {
        setWinner(players[1].name);
        setGameOver(true);
        return;
      }
    }
  };

  const handleRestart = () => {
    setBoxes(boxes.map((box) => ({ ...box, mark: '' })));
    setTurn(0);
    setWinner('');
    setGameOver(false);
  };

  return (
    <div className="h-screen bg-gray-900 flex flex-col items-center justify-center">
      <h1 className="text-3xl text-red-500 mb-4">Tic Tac Toe</h1>
      {players.length > 0 && (
        <p className="text-lg text-gray-200 mb-4">
          Player {players[turn].name}'s turn
        </p>
      )}
      <div className="grid grid-cols-3 gap-4">
        {boxes.map((box) => (
          <div
            key={box.id}
            className="w-20 h-20 rounded-full bg-gray-700 flex items-center justify-center cursor-pointer"
            onClick={() => handleBoxClick(box.id)}
          >
            <p className="text-3xl text-red-500">{box.mark}</p>
          </div>
        ))}
      </div>
      {gameOver && (
        <div className="mt-4">
          <p className="text-lg text-gray-200">
            Player "{winner}" wins! Congratulations!
          </p>
          <button
            className="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded"
            onClick={handleRestart}
          >
            Restart
          </button>
        </div>
      )}
    </div>
  );
};

export default TicTacToe;
